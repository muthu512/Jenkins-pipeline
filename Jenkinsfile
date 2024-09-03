pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add build steps here (e.g., compile code)
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                // Add test steps here (e.g., run unit tests)
                sh 'python3 -m unittest discover -s tests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add deployment steps here (e.g., deploy to a server)
            }
        }
    }
}

