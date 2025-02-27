pipeline {
    agent any

    environment {
        HELM_HOME = "$HOME/.helm"
        HELM_REPO = "bitnami"
        HELM_CHART = "wordpress"
        RELEASE_NAME = "my-wordpress"
        CHART_VERSION = "24.1.13"
        NAMESPACE = "wordpress-ns"
        SERVICE_TYPE = "NodePort"
        HELM_CMD = "/snap/bin/helm"
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    echo 'Checking out source code...'
                }
            }
        }

        stage('Setup Helm') {
            steps {
                script {
                    sh 'alias helm=${HELM_CMD}'
                    sh 'helm version'
                }
            }
        }

        stage('Deploy WordPress') {
            steps {
                script {
                    sh '''
                    alias helm=${HELM_CMD}
                    helm repo add ${HELM_REPO} https://charts.bitnami.com/${HELM_REPO}
                    helm repo update
                    helm install ${RELEASE_NAME} ${HELM_REPO}/${HELM_CHART} \
                        --version ${CHART_VERSION} \
                        --namespace ${NAMESPACE} \
                        --set service.type=${SERVICE_TYPE}
                    '''
                }
            }
        }
    }
}
