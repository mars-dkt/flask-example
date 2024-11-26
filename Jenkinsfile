environment {
    productName = "mgmt"
    componentName = "coffeepot"
    // The branch name is filtered to remove invalid Docker tag characters
    imageTag = "${env.DOCKER_ARTIFACT_REGISTRY}/${productName}-${componentName}:${env.BRANCH_NAME.toLowerCase().replaceAll('[^a-z0-9\\.\\_\\-]', '-')}-${env.BUILD_NUMBER}"
}
node {
     stage('Clone repository') {
         checkout scm
     }
     stage('Build image') {
        echo "Building Docker image using Dockerfile with tag"
        sh "docker build --tag=asia-northeast3-docker.pkg.dev/dev-settlement-onepage-project/dev-onepage-kr-ar/quickstart-image:tag${env.BUILD_NUMBER} ."
     }
     stage('Push image') {
            sh "gcloud auth configure-docker asia-northeast3-docker.pkg.dev"
            sh "docker push asia-northeast3-docker.pkg.dev/dev-settlement-onepage-project/dev-onepage-kr-ar/quickstart-image:tag${env.BUILD_NUMBER}"
     }
}
