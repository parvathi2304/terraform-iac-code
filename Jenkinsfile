pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-user/simple-terraform-demo.git'  // Replace with your Git repo URL
            }
        }

        stage('Install Terraform') {
            steps {
                script {
                    // Install Terraform if it's not already available
                    sh 'curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor > /usr/share/keyrings/hashicorp-archive-keyring.gpg'
                    sh 'sudo apt update && sudo apt install terraform'
                }
            }
        }

        stage('Initialize Terraform') {
            steps {
                script {
                    // Initialize Terraform
                    sh 'terraform init terraform/'
                }
            }
        }

        stage('Apply Terraform') {
            steps {
                script {
                    // Apply Terraform configuration to create the Docker container
                    sh 'terraform apply -auto-approve terraform/'
                }
            }
        }

        stage('Test Flask Application') {
            steps {
                script {
                    // Test the Flask app running on port 5000
                    sh 'curl http://localhost:5000'
                }
            }
        }
    }
}
