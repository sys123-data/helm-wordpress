pipeline {
    agent any

    environment {
        HELM_REPO = "bitnami"
        HELM_CHART = "wordpress"
        RELEASE_NAME = "my-wordpress"
        CHART_VERSION = "24.1.13"
        NAMESPACE = "wordpress-ns"
        SERVICE_TYPE = "NodePort"
    }

    stages {
       


        stage('Deploy WordPress') {
            steps {
                script {
                    sh '''
                    export KUBECONFIG=/home/hack/.kube/config
                    helm install ${RELEASE_NAME} ${HELM_REPO}/${HELM_CHART} \
                        --version ${CHART_VERSION} \
                        --namespace ${NAMESPACE} \
                        --set service.type=${SERVICE_TYPE}
                    '''
                    // helm install my-wordpress bitnami/wordpress --version 24.1.13 --namespace wordpress-ns --set service.type=NodePort

                }
            }
        }
    }
}
