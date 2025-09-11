pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/dev']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ahmedhamraj/taxi-booking.git']])
            }
        }
        stage('Build'){
            steps{
                sh "mvn package"
            }
        }
        stage('Deploy to tomcat'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat-credentials', path: '', url: 'http://172.31.19.242:8080/')], contextPath: 'taxibooking', war: '**/*.war'
            }
        }
    }
}
