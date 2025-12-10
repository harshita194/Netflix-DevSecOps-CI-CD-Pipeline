pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/harshita194/Netflix-DevSecOps-CI-CD-Pipeline.git'
            }
        }

        stage("Install Dependencies") {
            steps {
                sh 'npm install'
            }
        }

        stage("Run Security Scans") {
            steps {
                sh 'npm audit --audit-level=critical || true'
            }
        }

        stage("Build Docker Image") {
            steps {
                sh 'docker build -t netflix-app .'
            }
        }

        stage("Push to EC2 & Deploy") {
            when {
                expression { return params.DEPLOY_TO_EC2 == true }
            }
            steps {
                sh '''
                ssh -o StrictHostKeyChecking=no ubuntu@$EC2_IP "cd ~/app && git pull && ./deploy.sh"
                '''
            }
        }

        stage("Deploy to Vercel") {
            when {
                expression { return params.DEPLOY_TO_VERCEL == true }
            }
            steps {
                sh '''
                npm i -g vercel
                vercel --prod --yes
                '''
            }
        }
    }

    parameters {
        booleanParam(name: 'DEPLOY_TO_EC2', defaultValue: true)
        booleanParam(name: 'DEPLOY_TO_VERCEL', defaultValue: false)
    }
}
