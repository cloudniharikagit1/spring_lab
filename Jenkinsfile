pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/devopswithcloud/spring-petclinic.git']]])
            }
        }

        stage('Build') {
            steps {
                withMaven(maven: 'Maven 3.8.3', mavenSettingsConfig: 'my-maven-settings') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts(artifacts: '**/target/*.jar', allowEmptyArchive: true)
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
        }
    }
}
