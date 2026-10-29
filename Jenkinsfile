pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SRSoham/devops-pbl-set5-Copy.git'
            }
        }

        stage('Build with Maven') {
            steps {
                withEnv([
                    'JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64',
                    'PATH+JAVA17=/usr/lib/jvm/java-17-openjdk-amd64/bin'
                ]) {
                    sh 'java -version'
                    sh 'javac -version'
                    sh 'mvn -B clean package -DskipTests'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-pbl-set5:1.0 .'
            }
        }

        stage('Verify Docker Image') {
            steps {
                sh 'docker images devops-pbl-set5:1.0'
            }
        }
    }

    post {
        success {
            echo 'Q2 Jenkins pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the console output.'
        }
    }
}
