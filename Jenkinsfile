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
           pip install --no-cache-dir --upgrade setuptools boman-cli
           which boman-cli
           boman-cli -a run -cicd jenkins -at dbc504c9-cdd4-4aad-8a05-27b891bc13f6 -ct b93b0db3-ed63-4dac-85c4-19d7b99d716e'''
        }
      }
  }
}
