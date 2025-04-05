pipeline {
    agent any

    tools {
        maven 'Maven3.9' // Or whatever name you configured in Jenkins
    }

    options {
        skipStagesAfterUnstable()
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Run App') {
            steps {
                bat 'java -jar target\\auth-course-0.0.1-SNAPSHOT.jar'
            }
        }
    }
}
