pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull from GitHub or assume it's already checked out
                echo 'Code checked out'
            }
        }

        stage('Compile') {
            steps {
                sh 'mkdir -p build'
                sh 'javac -d build HelloWorld.java HelloWorldTest.java'
            }
        }

        stage('Test') {
            steps {
                echo 'Running test cases...'
                sh 'java -cp build HelloWorldTest'
            }
        }

        stage('Package JAR') {
            steps {
                sh 'jar cvf build/hello-world.jar -C build .'
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
