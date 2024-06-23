pipeline {
    agent {
        docker { image 'kantin10/terraform-aws-cli:v1'}
            
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

        stage('Terraform Refresh') {
            steps {
                sh 'terraform refresh -var-file=secret.tfvars'
            }
        }

        stage('Terraform Format') {
            steps {
                sh 'terraform fmt'
            }
        }

        stage('Terraform Validate') {
            steps {
                sh 'terraform validate -var-file=secret.tfvars'
            }
        }

        stage('Terraform Graph') {
            steps {
                sh 'terraform graph -var-file=secret.tfvars'
            }
        }

        stage('Terraform plan') {
            steps {
                sh 'terraform plan -var-file=secret.tfvars'
            }
        }
        stage('Terraform Apply') {
            steps {
                sh 'terraform apply -var-file=secret.tfvars --auto-approve'
            }
        }
    }
}
