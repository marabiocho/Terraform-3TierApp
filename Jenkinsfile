pipeline {
    agent any

    environment {
        TERRAFORM_HOME = tool name: 'Terraform', type: 'TerraformInstallation'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/marabiocho/Terraform-3TierApp.git', branch: 'main'
            }
        }

        stage('Terraform Init') {
            steps {
                dir('Terraform-3TierApp') {
                    sh "${TERRAFORM_HOME}/bin/terraform init"
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                dir('Terraform-3TierApp') {
                    sh "${TERRAFORM_HOME}/bin/terraform plan"
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                dir('Terraform-3TierApp') {
                    sh "${TERRAFORM_HOME}/bin/terraform apply -auto-approve"
                }
            }
        }
    }
}
