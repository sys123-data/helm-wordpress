// steps to build wordpress in k8s using helm
pipeline {
    agent any
    environment {
        // define the namespace
        NAMESPACE = "wordpress-ns"
        // define the helm chart name
        HELM_CHART = "bitnami/wordpress"
        // define the helm release name
        RELEASE_NAME = "my-wordpress"
        // define the version of the wordpress app
        WORDPRESS_VERSION = "24.1.13"
        // service type
        SERVICE_TYPE = "NodePort"
        // define the helm values file
        // VALUES_FILE = "values.yaml"
    }
    stages {
        stage('Checkout') {
            steps {
                // checkout the code from the repository
                git 'https://github.com/sys123-data/helm-wordpress.git'
            }
        stage('Deploy Wordpress App') {
            steps {
                // deploy the helm chart
                script {
                    // create the namespace 
                    sh "kubectl create namespace ${NAMESPACE}"
                    // deploy the helm chart
                    // helm install my-wordpress bitnami/wordpress --version 24.1.13 --namespace wordpress-ns --set service.type=NodePort
                    sh "helm install ${RELEASE_NAME} ${HELM_CHART} --version ${WORDPRESS_VERSION} --namespace ${NAMESPACE} --set service.type=${SERVICE_TYPE}"
                }
            }
        }
        }
    }
}