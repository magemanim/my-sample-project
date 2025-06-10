pipeline {
    agent any
    
    // Add tools configuration
    tools {
        maven 'Maven-3.9.10' // Must match exact name from Jenkins Global Tool Configuration
    }
    
    environment {
        DEPLOY_DIR = "/opt/tomcat/webapps"
    }

    stages {
        stage('Clone Code') {
            steps {
                git url: 'https://github.com/magemanim/my-sample-project.git',
            }
        }

        stage('Build WAR with Maven') {
            steps {
                sh 'mvn clean package'
                // Consider adding test execution
                // sh 'mvn test' 
            }
        }            
            // Optional post-build actions for this stage
            post {
                success {
                    archiveArtifacts artifacts: 'target/*.war', fingerprint: true
                }
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
            // You could add deployment steps here
        }
        failure {
            echo 'Build failed!'
            // Consider adding email notification
            // emailext body: 'Build failed!', subject: 'Build Failed', to: 'team@example.com'
        }
    }
}
