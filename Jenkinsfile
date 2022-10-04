pipeline {
    agent any
    parameters {
        choice(name: 'mode', choices: ['plan', 'apply'], description: 'Select Plan or Apply')
    }
    stages {
        stage('init') {
             steps {
                sh '''
                /usr/local/bin/terraform init 
                '''
            }
        }
        stage('validate') {
             steps {
                sh '''
               /usr/local/bin/terraform validate
               '''
            }
        }
        stage('Terraform plan') {
              steps {
                 sh '''
                echo "/usr/local/bin/terraform plan -lock=false"
                '''
            }
        }

        stage('Terraform apply') {
            when {
                equals expected: "apply", actual: env.mode
            }
            steps {
                sh '''
                echo "/usr/local/bin/terraform apply -lock=false -auto-approve"
                '''
            }
        }

    }
}
