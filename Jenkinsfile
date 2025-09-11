pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/dev']],
                    extensions: [],
                    userRemoteConfigs: [[url: 'https://github.com/ahmedhamraj/taxi-booking.git']]
                )
            }
        }

        stage('Build') {
            steps {
                dir('taxi-booking') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                dir('taxi-booking') {
                    deploy adapters: [
                        tomcat9(
                            credentialsId: 'tomcat-credentials',
                            path: '',
                            url: 'http://172.31.19.242:8080/'
                        )
                    ],
                    contextPath: 'taxibooking',
                    war: 'target/taxi-booking-1.0.1.war'
                }
            }
        }
    }
}
