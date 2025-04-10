pipeline{
    agent any
    tools{
        terraform 'terraform'
    }

    stages{
        stage("Checkout from git"){
            steps{
                git branch:'main', url: 'https://github.com/mpramakrishnareddy/cicd1.git'
            }
        }
        stage("Terraform init"){
            steps{
                sh 'terraform init'
            }
        }
        stage("Terraform plan"){
            steps{
                sh 'terraform plan'
            }
        }
        stage("Terraform apply"){
            steps{
                sh 'terraform apply'
            }
        }

        // stage("Terraform destroy"){
        //     steps{
        //         sh 'terraform destroy --auto-approve'
        //     }
        // }

    }


}