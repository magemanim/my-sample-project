pipeline {
    agent any

    tools {
        maven 'Maven-3.9.10'   // As configured in Jenkins Global Tools
    }

    environment {
        DEPLOY_DIR = "/opt/tomcat/webapps"
    }

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/magemanim/my-sample-project.git'
            }
        }

        stage('Build WAR with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy WAR to Tomcat') {
            steps {
                sh 'cp target/*.war $DEPLOY_DIR'
                echo 'WAR file deployed to Tomcat!'
            }
        }
    }

    post {
        success {
            echo 'Build & Deployment successful!'
        }
        failure {
            echo 'Something went wrong!'
        }
    }
}
