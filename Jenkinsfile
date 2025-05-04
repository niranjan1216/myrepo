pipeline {
    agent any

    stages {
        stage('Compile') {
            steps {
                echo 'Compiling Java files...'
                bat 'javac HelloWorld.java HelloWorldTest.java'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'java HelloWorldTest'
            }
        }

        stage('Package JAR') {
            steps {
                echo 'Packaging into JAR...'
                bat 'jar cvf hello-world.jar *.class'
            }
        }

        stage('Run JAR') {
            steps {
                echo 'Running the packaged JAR...'
                bat 'java -cp hello-world.jar HelloWorld'
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
            bat 'del /Q *.class'
        }
    }
}
