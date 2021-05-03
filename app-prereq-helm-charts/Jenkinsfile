pipeline {
    agent any

    stages {

       stage('Git Clone') {
          steps {
                checkout scm
            }
        }

        stage('Get cluster-info') {
            steps{
                script {
                    withKubeConfig([credentialsId: 'kubernetesCred',serverUrl: "${ServerUrl}"]) {
                        sh "kubectl  cluster-info"
                    }
                }
            }
        }

        stage('Helm kafka upgrade') {
            steps{
                script {
                    withKubeConfig([credentialsId: 'kubernetesCred',serverUrl: "${ServerUrl}"]) {
                        sh "helm upgrade kafka  --namespace kafka ./helm/kafka/"
                    }
                }
            }
        }

    }
}