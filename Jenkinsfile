pipeline {
    agent any

    environment {
        K8S_TOKEN = '<your-token>'
        K8S_CA   = '<your-base64-ca>'
        K8S_SERVER = 'https://2DBCD6BD06BA547776EAC8ED5902179A.gr7.ap-south-1.eks.amazonaws.com'
    }

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                sh '''
                    echo $K8S_CA | base64 --decode > /tmp/eks-ca.crt
                    kubectl apply -f deployment-service.yml \
                        --token=$K8S_TOKEN \
                        --certificate-authority=/tmp/eks-ca.crt \
                        --server=$K8S_SERVER \
                        -n webapps
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    kubectl get svc -n webapps \
                        --token=$K8S_TOKEN \
                        --certificate-authority=/tmp/eks-ca.crt \
                        --server=$K8S_SERVER
                '''
            }
        }
    }
}
