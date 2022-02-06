pipeline {
    agent {
        label "kubectl"
    }

    stages {
        stage('Deploy') {
            steps {
                git url: 'https://github.com/Cervator/backstage-template-jenkins.git'
                withKubeConfig(clusterName: 'cluster-1', credentialsId: 'backstage-sa-token-avst', serverUrl: 'https://34.132.60.24') {
                    sh '''
                        whoami
                        ls -la
                        echo "$SHELL"
                        which kubectl
                        kubectl version
                        kubectl get pods -n backstage
                        kubectl apply -f jenkins-statefulset.yaml -n backstage
                        kubectl apply -f jenkins-service.yaml -n backstage
                        kubectl get svc -n backstage
                        sleep 15
                        kubectl get svc -n backstage
                        sleep 15
                        kubectl get svc -n backstage
                        sleep 15
                        kubectl get svc -n backstage
                    '''
                }
            }
        }
    }
}
