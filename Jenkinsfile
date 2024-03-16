pipeline {
   agent any
triggers {
  pollSCM '* * * * *'
}
parameters {
  choice choices: ['DEV', 'QA'], name: 'ENVIRONMENT'
}

   stages {
     stage('checkout') {
       steps {
               checkout scm
             }}
     stage('Build') {
       steps {
              sh '/home/ishika/Documents/devops_software/apache-maven-3.9.6/bin/mvn install'
             }}
     stage('Deployment') {
       steps {
             sh 'cp target/slack-notification.war /home/ishika/Documents/devops_software/apache-tomcat-9.0.85/webapps'
             }} 
     stage('slack-notification') {
       steps {
             slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'devops-2', color: 'good', message: 'This is jenkins slack notification test', teamDomain: 'student-work', tokenCredentialId: 'slack-notification'
             }}
}}
  
