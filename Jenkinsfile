pipeline {
    agent { 
        node {
            label 'docker_python_agent'
            }
      }
    triggers {
      pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                echo "Starting build..."
                cd myapp
                python3 -m venv venv
                . venv/bin/activate 
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                echo "Testing..."
                cd myapp
                python3 fire.py
                python3 fire.py --name=jarhead
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}