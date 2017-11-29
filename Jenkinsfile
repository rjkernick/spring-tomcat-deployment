pipeline {
    agent any

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

        stage('Build'){
            steps{
                sh 'mvn package'
            }
        }


    }
}