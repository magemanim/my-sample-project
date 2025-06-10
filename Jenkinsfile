pipeline {
    agent any

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
                sh 'sudo mvn clean package'
            }
        }

    }

    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Something went wrong!'
        }
    }
}
