pipeline {
    agent any
    tools {
        jdk 'JDK17'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/ericvelez28733/jenkindemo.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Spring Boot project with Gradle...'
                sh './gradlew clean build'
            }
            post {
                success {
                    echo '✅ Build successful — JAR file created!'
                }
                failure {
                    echo '❌ Build failed! Please check logs.'
                }
            }
        }

        stage('Archive Artifact') {
            steps {
                echo 'Archiving built JAR artifact...'
                archiveArtifacts artifacts: '**/build/libs/*.jar', fingerprint: true
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulating deployment (placeholder for demo)...'
                sh 'echo "Deploying app locally..."'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete.'
        }
        success {
            echo '✅ Pipeline finished successfully.'
        }
        failure {
            echo '❌ Pipeline failed. Please fix errors and retry.'
        }
    }
}
