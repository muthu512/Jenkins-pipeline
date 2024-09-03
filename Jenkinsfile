pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'               
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'             
                sh 'python3 -m unittest discover -s tests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}

