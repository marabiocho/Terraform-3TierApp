pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'kantin10/terraform-aws-cli'
                    // Run the container on the node specified at the
                    // top-level of the Pipeline, in the same workspace,
                    // rather than on a new node entirely:
                    reuseNode true
                }
            }
            steps {
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
    }
}
