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
           sh 'pip install --no-cache-dir --upgrade boman-cli'
           sh '~/.local/bin/boman-cli -a run -at dbc504c9-cdd4-4aad-8a05-27b891bc13f6 -ct b93b0db3-ed63-4dac-85c4-19d7b99d716e'
        }
      }
  }
}
