pipeline {
    agent any 
    tools {
        maven 'Maven-3.8.8'
    }
    stages{
        stage ('clone') {
            steps {
                git branch: 'main', url: 'https://github.com/cloudniharikagit1/spring-petclinic.git'
            }
        }
        stage ('build')
        steps {
            sh "mvn clean pacakge -Dmaven.test.failure.ignore=true" 
        }
        
    }
}
   
   
