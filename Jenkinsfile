pipeline {
    agent any

    tools {
        jdk 'JDK17'
        maven 'Maven3'
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
                echo 'Building Spring Boot project...'
                sh 'mvn clean package -DskipTests'
            }
            post {
                success {
                    echo 'Build successful — JAR file created!'
                }
                failure {
                    echo 'Build failed! Please check logs.'
                }
            }
        }

        stage('Archive Artifact') {
            steps {
                echo 'Archiving built JAR artifact...'
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }

        stage('Deploy Simulation') {
            steps {
                echo 'Simulating deployment (placeholder for demo)...'
                sh 'echo "Deploying app to local container..."'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete.'
        }
        success {
            echo '✅ Build pipeline finished successfully.'
        }
        failure {
            echo '❌ Build pipeline failed. Please fix errors and retry.'
        }
    }
}
