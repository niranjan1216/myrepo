pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code checked out'
                // Assuming code is already pulled via SCM
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling Java files...'
                sh 'javac HelloWorld.java HelloWorldTest.java'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'java HelloWorldTest'
            }
        }

        stage('Package JAR') {
            steps {
                echo 'Packaging into JAR...'
                sh 'jar cvf hello-world.jar *.class'
            }
        }

        stage('Run JAR') {
            steps {
                echo 'Running the packaged JAR...'
                sh 'java -cp hello-world.jar HelloWorld'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: '*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            sh 'rm -f *.class'
        }
    }
}


        stage('Run JAR') {
            steps {
                echo 'Running the JAR file...'
                sh 'java -cp build/hello-world.jar HelloWorld'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build/*.jar', fingerprint: true
            }
        }
    }
}
