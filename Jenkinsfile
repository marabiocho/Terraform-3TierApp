pipeline {
    agent {
        docker {
            image 'kantin10/terraform-aws-cli:latest'
            args '-u root:root' // Run as root user to avoid permission issues
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/marabiocho/Terraform-3TierApp.git', branch: 'main'
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
    }
}
