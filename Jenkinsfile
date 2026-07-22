pipeline {
    agent{
        label 'Agent-1'
    }
    options{
        timeout(time: 10 , unit: 'MINUTES')
    }
    parameters{

        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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
                   echo "Hello ${params.PERSON}"

                    echo "Biography: ${params.BIOGRAPHY}"

                    echo "Toggle: ${params.TOGGLE}"

                    echo "Choice: ${params.CHOICE}"

                    echo "Password: ${params.PASSWORD}"
                    echo "Added webhook
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
        aborted {
            echo "Pipeline aborted due to timeout"
        }
    }
}