pipeline{
    agent any
    // tools{
    //     terraform 'terraform'
    // }
    environment{
        AWS_ACCESS_KEY_ID = credentials("AWS_ACCESS_KEY_ID")
        AWS_SECRET_ACCESS_KEY = credentials("AWS_SECRET_ACCESS_KEY")
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
                sh 'terraform plan -out=tfplan'
            }
        }
        stage("Terraform apply"){
            steps{
                input message: 'Apply changes from plan?'
                // sh 'terraform apply tfplan'
                //sh 'TF_LOG=INFO terraform apply -auto-approve tfplan' //detailed logs in Jenkins output
                //sh 'terraform apply -auto-approve tfplan | tee apply.log' //tee or force output flush, Archive Terraform Logs
                //sh(script: 'terraform apply -auto-approve tfplan', returnStdout: true) // force output flush


                sh 'terraform apply -auto-approve tfplan'

            }
        }

        stage("Terraform destroy"){
            steps{
                sh 'terraform destroy --auto-approve'
            }
        }

    }


}