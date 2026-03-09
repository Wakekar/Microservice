pipeline {
    agent any

    environment {
        K8S_TOKEN  = 'eyJhbGciOiJSUzI1NiIsImtpZCI6IjdXM3d2WTNmSXlaZndmUTJKRjhQMktTMi00ZkxfLVRWU0p3NnpOTm00cWcifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJ3ZWJhcHBzIiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZWNyZXQubmFtZSI6ImplbmtpbnMtdG9rZW4iLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC5uYW1lIjoiamVua2lucyIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VydmljZS1hY2NvdW50LnVpZCI6ImU2MzZiMTYyLTRmODctNGIyZS1hNGJhLWE3YWUwY2RhMTEwMiIsInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDp3ZWJhcHBzOmplbmtpbnMifQ.Z_D1fewE0mhaf6dnAnQn2N8pBqwg9n32Myd-BkDVpVnzSbDvH2s5yNwhcOEpq0jbT0MJnt9NtzxhR-p5YLYdSn5YWOJ4mzFsiNdTPfqGeyviT16hifxtaNuEm7cQBNqr8tnEGFtcvyRBpHITbyq2urbBV50Rz1hbVSt-g98swssfVeO0c_-qQODucnWjrGcmSxHiW8IFTwVP4065999LtQJu1nU-Pm3Xx5M5mpwX2d9MgXpzmj_tNn7_pH6urfmmK5-xkA8D7f-RNpfqzAesfqXNP943C3qOH2CFysfl3ffVTgSChG1iWKWMA4KtICT3t2MCXP36unQI5su_tWPW3Q'
        K8S_CA     = '''LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURCVENDQWUyZ0F3SUJBZ0lJUEZnZUtLSVd6NTh3RFFZSktvWklodmNOQVFFTEJRQXdGVEVUTUJFR0ExVUUKQXhNS2EzVmlaWEp1WlhSbGN6QWVGdzB5TmpBek1Ea3hOakl6TURWYUZ3MHpOakF6TURZeE5qSTRNRFZhTUJVeApFekFSQmdOVkJBTVRDbXQxWW1WeWJtVjBaWE13Z2dFaU1BMEdDU3FHU0liM0RRRUJBUVVBQTRJQkR3QXdnZ0VLCkFvSUJBUURxdnNROGxQTjhFSDBGMzNqTUw1Q2haRlNqNDh2Ym11K2ErSkUrOGQ1TXQ4RE41d3lrY2ZQb3FvczEKUGlhcDRIYXdEam1BbDhDMW80MVp4dDFVczBvYXl4Q3A0QW9LU0NUaExsZUhyNWJSdmN3bVJCL2M5eTViSWs0agpzWUIrMlMrV3pDaW03RlZOZDJwMFJKazM1Vk5OZWhTdkNuUHo1R0U4LzZCSzUrRWNubzlLNjFTZmVDd1dvV1d6CjBCNkhRTTVXQWIxNi9FZnRxSUsyUENtYW4wbS9kQkdxdStWbVZacUZhelU5dzFPSW5SR0hTcHQrdy9PTG05bWwKeUU5RGNoZmI2OWY2SW1LUjkySnJmdkVNRWtFeGxOMVMvT2dHZWhFYlNFSkpzOVhsbit5ZzI4VWlHKzNyUGo1YgphaUZqMUpzdTdEaWh1QlVCd2JQVzJTWm9aRWdyQWdNQkFBR2pXVEJYTUE0R0ExVWREd0VCL3dRRUF3SUNwREFQCkJnTlZIUk1CQWY4RUJUQURBUUgvTUIwR0ExVWREZ1FXQkJRbFdBeTF0R0JRejAreU5SSndYZWtZcXpPa3ZEQVYKQmdOVkhSRUVEakFNZ2dwcmRXSmxjbTVsZEdWek1BMEdDU3FHU0liM0RRRUJDd1VBQTRJQkFRQzE1cGkwaVZGWgptMy9TU3hoWW10VGdHc1dJaVlKZGtTQjNES3JrNkEwTlJVRHdEK2NnanI2Njg2dlJpUGdzQjZ5Z3FMeTNabkNxCjA2bjRNVEtPRkNwOWdsUEZvVFFZd1g4OGhydFc2dHMzK1V2Y29RTmU2QVdkVmRJYnB0UUl1QXZVRENJYjEyeVYKVk5td01Kd1hETUI0Q3J6M3hVcGRxcEpPYWJBK1ZZVXk3dXlWMDFrOWJGcEMzYzVEZC9LZjVxOTQzdHoyNmJhZApPT1dmakl0UnJmMnpIRjJENU1CWTlRd2xVa2c0YWdkV0krbWxpRVZWMGlNSlpnM09jd2E1VTIvQWVJbE1TdVN4CkJ4ekpLbTcvQ0huczBFTFpWYTRQZDBMMjF6eGJmTkI3anVhenB2b0VqTjRoZmtRUVM5ME1zUCt0aUc5bGNEb0oKWUQ2dFZjOWx3eWtxCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K'''
        K8S_SERVER = 'https://2DBCD6BD06BA547776EAC8ED5902179A.gr7.ap-south-1.eks.amazonaws.com'
        K8S_NAMESPACE = 'webapps'
    }

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                sh '''
                    echo "$K8S_CA" | base64 --decode > /tmp/eks-ca.crt
                    kubectl apply -f deployment-service.yml \
                        --token="$K8S_TOKEN" \
                        --certificate-authority=/tmp/eks-ca.crt \
                        --server="$K8S_SERVER" \
                        --namespace="$K8S_NAMESPACE"
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    kubectl get svc \
                        --token="$K8S_TOKEN" \
                        --certificate-authority=/tmp/eks-ca.crt \
                        --server="$K8S_SERVER" \
                        --namespace="$K8S_NAMESPACE"
                '''
            }
        }
    }
}
