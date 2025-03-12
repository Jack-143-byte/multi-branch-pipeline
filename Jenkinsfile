pipeline {
    agent any
    
    tools{
        maven 'Maven 3.9.7'
    }
    environment {
        TOMCAT_URL = 'http://139.59.7.205:8080/' // Replace with your Tomcat server URL
        TOMCAT_USER = 'tomcat' // Replace with your Tomcat username
        TOMCAT_PASSWORD = 'devops@123' // Replace with your Tomcat password
    }
    stages {
        stage ("code"){
            steps {
                git "https://github.com/Jack-143-byte/one.git"
            }
        }
        stage ("Build"){
            steps {
                sh 'mvn clean package'
            }
        
        stage ('Deploy to tomcat'){
            steps{
                sh """
                    curl -v -u ${TOMCAT_USER}:${TOMCAT_PASSWORD} \
                    -T target/*.war \
                    ${TOMCAT_URL}/manager/text/deploy?path=/yourapp&update=true
                """
            }
        }
    }
}


