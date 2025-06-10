pipeline {
    agent any

    tools {
        maven 'Maven-3.8.6'   // As configured in Jenkins Global Tools
    }

    environment {
        DEPLOY_DIR = "/opt/tomcat/webapps"
    }

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/your-user/sample-java-project.git'
            }
        }

        stage('Build WAR with Maven') {
            steps {
                sh 'mvn clean package'
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
