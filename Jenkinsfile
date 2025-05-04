pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/niranjan1216/myrepo.git'
            }
        }

        stage('Build') {
            steps {
                echo "build completed"
            }
        }

        stage('Test') {
            steps {
               echo "test Completed"
            }
        }

        stage('Package') {
            steps {
                echo "package done "
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
