pipeline {
    agent any

    stages {
        stage('deploy to kubernetes') {
            steps {
            withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9DA96DB290A8C15F367BD88606BB42AF.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
             
            }
            }
        }
        
        stage('verify Deployment') {
            steps {
            withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9DA96DB290A8C15F367BD88606BB42AF.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps"  
            }
            }
        }
    }
}
