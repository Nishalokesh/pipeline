pipeline {
    agent any

    environment {
        GIT_REPO_URL = 'https://github.com/Nishalokesh/pipeline.git'
        NGINX_PATH = 'C:\\Users\\lnish\\Downloads\\nginx-1.24.0\\nginx-1.24.0\\htmldocs'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Use the checkout step to clone the Git repository
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url:GIT_REPO_URL]]])
                }
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    // Using the Jenkins workspace variable to reference files
                    bat 'xcopy /y "file:///C:/Users/lnish/OneDrive/Desktop/jenkins_pipeline/pipeline.html" "%NGINX_PATH%"'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! You can add additional steps here.'
        }
        failure {
            echo 'Pipeline failed! You may want to take some actions.'
        }
    }
}
