pipeline {
    agent any

    tools {
        maven 'mvn3'
        jdk 'jdk8'
    }

    environment {
        MVN_PROPS = credentials('tomcat-creds')
    }

    stages {
        stage('Checkout'){
            steps{
                checkout scm
            }
        }

        stage('Build'){
            steps{
                sh 'mvn package'
            }
        }

        stage('Test') {
            steps {
                sh 'echo $tomcat_url'
                sh 'echo $MAVEN_HOME'
            }
        }
    }
}