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
                sh 'scp target/*.war ubuntu@18.204.216.196:/home/ubuntu/apache-tomcat-10.1.36/webapps'
            }
        }
    }
}

