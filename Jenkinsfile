pipeline {
    agent{
        label 'Agent-1'
    }

    environment{
        course ="Devops"
    }
    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/HarinadhKamma/Jenkins_practise.git'
            }
        }

        stage('Build') {
            steps {
              script{
                sh """
                  echo "build"
                  echo $course
                  env
                """ 
              }  
                echo 'Building the application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline Completed'
            cleanWs()
        }

        success {
            echo 'Build Successful'
        }

        failure {
            echo 'Build Failed'
        }
    }
}