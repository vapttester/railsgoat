pipeline{
  agent any
  stages{
       stage('Debug') {
            steps {
                sh 'hostname'
                sh 'whoami'
                sh 'ls -l /usr/bin/docker || echo "Docker binary not here"'
            }
       }
      stage('Bomanai'){
        steps{
           sh '''python3.12 -m venv /opt/boman-env
           . /opt/boman-env/bin/activate
           pip install "setuptools<70.0.0"
           pip install --no-cache-dir --upgrade boman-cli
           which boman-cli
           boman-cli -a run -cicd jenkins -at 9db3c849-8b34-41e5-aebd-279118b7d033 -ct 41bb9111-e57f-43d9-aa15-8c2e751ddb36'''
        }
      }
  }
}
