pipeline {
    agent any
    tools {
        maven 'Maven 3.8.1' // Use installed Maven
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Darshanm416/java-maven.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'scp -o StrictHostKeyChecking=no target/*.war jenkins@44.202.142.249:/opt/tomcat/apache-tomcat-10.1.39/webapps/'
                sh 'ssh -o StrictHostKeyChecking=no jenkins@44.202.142.249 "sudo systemctl restart tomcat"'
            }
        }
    }
}

