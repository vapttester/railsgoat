pipeline{
  agent any
  stages{
       stage('Debug') {
            steps {
                sh 'hostname'
                sh 'whoami'
                sh 'ls -l /usr/bin/docker || echo "Docker binary not here"'
                sh 'ls -la'
            }
       }
    stage('presetup'){
      steps{
        
        sh '''
        python3.12 -m venv /opt/boman-env
        . /opt/boman-env/bin/activate
        
        # 1. Clear out the bridge folder
        rm -rf /c/jenkins_temp/scan
        mkdir -p /c/jenkins_temp/scan
        
        # 2. Copy your code from Jenkins to the Windows Bridge
        cp -r "$WORKSPACE"/* /c/jenkins_temp/scan/
        
        # 3. Move into the bridge folder and run the scan
        cd /c/jenkins_temp/scan/
      
        '''
      }
    }
      stage('Bomanai'){
        steps{
           sh '''
           pip install "setuptools<70.0.0"
           pip install --no-cache-dir --upgrade boman-cli
           pwd
           
          '''
        }
      }
  }
}
