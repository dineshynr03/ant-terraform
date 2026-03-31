cat << 'EOF' > Jenkinsfile

pipeline {

    agent any



    environment {

        AWS_REGION = 'ap-south-1'

        TF_CLI_ARGS = "-no-color"

    }



    stages {

        stage('Checkout') {

            steps {

                checkout scm

            }

        }



        stage('Terraform Init') {

            when {

                branch 'develop'

            }

            steps {

                echo 'Initializing Terraform...'

                sh 'terraform init'

            }

        }



        stage('Terraform Plan') {

            when {

                branch 'develop'

            }

            steps {

                echo 'Generating Plan...'

                sh 'terraform plan -out=develop.tfplan'

            }

        }



        stage('Terraform Apply') {

            when {

                branch 'main'

            }

            steps {

                echo 'Applying Changes...'

                sh 'terraform apply -auto-approve'

            }

        }

    }

}

EOF

