pipeline {
    agent { label 'AGENT-1'}
    environment {
        PROJECT = 'expense'
        COMPONENT = 'backend'
        DEPLOY_TO = 'QA'
        REGION = 'us-east-1'
    }
    options {
        disableConcurrentBuilds ()
        timeout(time: 30, unit: 'MINUTES')
    }
    parameters {
        string(name: 'version', description: 'Please Enter the application version')
    }

    stages {
        stage('Deploy') {        
            }
            steps {
                script{
                    withAWS(region: 'us-east-1', credentials: 'aws-creds') {
                        sh """
                            aws eks update-kubeconfig --region $REGION --name expense-dev
                            kubectl get nodes
                        """
                    }
                }
            }
        }
        
    }
    post {
        always {
            echo "I will always say hello-again"
            deleteDir()
        }
        failure {
            echo "I will run when pipeline fails"
        }
        success {
            echo "I will run when pipeline succeeds"
        }
    }
}