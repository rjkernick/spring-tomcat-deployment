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

        stage("Setup Maven"){
            steps{
                sh 'cp $MVN_PROPS ${MAVEN_HOME}/conf/'
            }
        }

        stage('Build'){
            steps{
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mvn tomcat7:deploy -Dtomcat.url=$tomcat_url'
            }
        }
    }
}