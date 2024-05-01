pipeline {
    agent any 
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh '/home/viplav/Documents/maven/apache-maven-3.9.6/bin/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                sh 'cp target/honda.war /home/viplav/Documents/maven/apache-tomcat-9.0.88/webapps'
            }
        }
        
        stage('slack') {
            steps {
                slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'honda', color: 'good', message: 'welcome to honda', notifyCommitters: true, teamDomain: 'devops', tokenCredentialId: '6f5fd33d-fdd0-450f-8461-0daff9768672'
            }
        }
    }
}
