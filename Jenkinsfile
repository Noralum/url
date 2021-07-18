
pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    tools {
        maven 'M2_HOME'
    }
    stages{
        stage('build'){
            steps{
            sh 'mvn clean'
            sh 'mvn install'
            sh 'mvn package'
            sh 'mvn test'
            
                
            }
        }
        stage ('tomcat deploy') {
            steps {
                deploy adapters: [tomcat8(credentialsId: 'TomcatID', path: '', url: 'http://192.168.1.99:8080/')], contextPath: null, war: '**/*.war'
            }

        }
    }


}