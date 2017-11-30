pipeline {
    agent any

    environment {
        MVN_PROPS_FILE = credentials('tomcat-creds')
    }

    tools {
        maven 'mvn3'
        jdk 'jdk8'
    }

    stages {
        stage('Checkout'){
            steps{
                checkout scm
            }
        }

        stage("Setup Maven"){
            steps{
//                sh "mkdir ${MAVEN_HOME}/conf/"
                sh 'cp $MVN_PROPS_FILE ${MAVEN_HOME}/conf/'
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