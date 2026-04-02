pipeline{
  agent any
  stages{
    stages {
        stage('Install System Dependencies') {
            steps {
                sh '''
                sudo apt-get update
                sudo apt-get install -y software-properties-common
                '''
            }
        }

        stage('Install Python 3.12 & Pip') {
            steps {
                sh '''
                # Add Python repository
                sudo add-apt-repository ppa:deadsnakes/ppa -y
                sudo apt-get update
                
                # Install Python 3.12 and venv (which includes pip logic)
                sudo apt-get install -y python3.12 python3.12-venv python3.12-dev
                
                # Install/Ensure Pip for 3.12
                curl -sS https://bootstrap.pypa.io/get-pip.py | python3.12
                
                python3.12 --version
                python3.12 -m pip --version
                '''
            }
        }

        stage('Install Docker') {
            steps {
                sh '''
                # Official Docker install script for convenience in CI
                if ! command -v docker &> /dev/null; then
                    curl -fsSL https://get.docker.com -o get-docker.sh
                    sudo sh get-docker.sh
                    sudo usermod -aG docker jenkins
                else
                    echo "Docker already installed"
                fi
                docker --version
                '''
            }
        }
    stage('Bomanai'){
      steps{
         sh 'python --version' 
         sh 'pip install --no-cache-dir --upgrade boman-cli'
         sh '~/.local/bin/boman-cli -a run -cicd jenkins -at dbc504c9-cdd4-4aad-8a05-27b891bc13f6 -ct b93b0db3-ed63-4dac-85c4-19d7b99d716e'
      }
    }
  }
}
