pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('Build') { 
            steps { 
                script{
                 app = docker.build("hellobhuvnesh")
                }
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }
        stage('Deploy') {
            steps {
                script{
                        docker.withRegistry('https://100918349305.dkr.ecr.us-east-1.amazonaws.com/hellobhuvnesh/', 'ecr:us-east-1:bhuvneshthakre') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }
                }
            }
        }
    }
}