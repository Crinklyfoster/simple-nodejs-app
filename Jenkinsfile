pipeline {
    agent any

    environment {
        NODE_HOME = tool name: 'NodeJS 14', type: 'NodeJS'
        PATH = "${env.NODE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/sreepathysois/simple-nodejs-app_Lab_Exam.git', branch: 'main'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build & Validate') {
            steps {
                echo 'No build step needed for static app.'
            }
        }

        stage('Test') {
            steps {
                echo 'No tests provided. Skipping.'
            }
        }

        stage('Package') {
            steps {
                archiveArtifacts artifacts: '**/*', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                sh 'nohup node server.js &'
                echo 'Application deployed and running.'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
        success {
            echo 'CI Pipeline completed successfully.'
        }
        failure {
            echo 'CI Pipeline failed.'
        }
    }
}
