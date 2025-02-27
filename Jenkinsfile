# steps to build wordpress in k8s using helm
pipeline {
    agent any
    environment {
        // define the namespace
        NAMESPACE = "wordpress"
        // define the helm chart name
        HELM_CHART = "bitnami/wordpress"
        // define the helm release name
        RELEASE_NAME = "wordpress"
        // define the helm values file
        // VALUES_FILE = "values.yaml"
    }
    stages {
        stage('Checkout') {
            steps {
                // checkout the code from the repository
                git '