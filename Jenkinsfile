pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/alkesh-007/jenkins.git'
            }
        }
        stage('initialize') {
            steps {
                sh 'terraform init'
            }
        }
        stage('terraform plan') {
            steps {
                sh 'terraform plan'
            }
        }
        stage('approval') {
            steps {
                input message: 'Do you want to apply the Terraform changes?', ok: 'Apply'
            }
        }
        stage('terraform apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
        stage('terraform destroy') {
            steps {
                input message: 'Do you want to destroy the Terraform resources?', ok: 'Destroy'
                sh 'terraform destroy -auto-approve'
            }
        }
    }
}