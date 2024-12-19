pipeline {
    agent any
       stages {
           stage('Deploy to Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BE1D4471F6264B2246C8708BAD1528E4.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                 }
            }
        }
        stage('Verify deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BE1D4471F6264B2246C8708BAD1528E4.gr7.ap-south-1.eks.amazonaws.com']]) {
                  sh "kubectl get svc -n webapps"
               }
            }
        }   
   }
}
