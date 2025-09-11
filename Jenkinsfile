pipeline {
    agent any

        stages {
        stage('Checkout') {
            steps {
                git branch: 'dev',
                    url: 'https://github.com/ahmedhamraj/spring-petclinic.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests -U'
            }
        }       
        stage('Deploy to Tomcat') {
            steps {
                   sh 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/taxi-booking/target/taxi-booking-1.0.1.war ubuntu@172.31.19.242:/var/lib/tomcat9/webapps/taxi-booking.jar'
            }
        }
    }
}
