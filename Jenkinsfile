pipeline {
    agent {
        docker {
            image 'kantin10/terraform-aws-cli'
            reuseNode true
        }
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    git url: 'https://github.com/marabiocho/Terraform-3TierApp.git', branch: 'main'
                }
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
