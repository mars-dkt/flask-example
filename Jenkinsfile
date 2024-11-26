node {
     stage('Clone repository') {
         checkout scm
     }
     stage('Build image') {
         app = docker.build("mars-dkt/flask-example")
     }
     stage('Push image') {
         docker.withRegistry('http://asia-northeast3-docker.pkg.dev/dev-settlement-onepage-project/dev-onepage-kr-ar/quickstart-image', 'credentials-id') {
             app.push("${env.BUILD_NUMBER}")
             app.push("latest")
         }
     }
}

stage('Build image') {
  app = docker.build("mars-dkt/flask-example")
}

stage('Push image') {
  docker.withRegistry('http://asia-northeast3-docker.pkg.dev/dev-settlement-onepage-project/dev-onepage-kr-ar/quickstart-image', 'credentials-id')
  {
     app.push("${env.BUILD_NUMBER}")
     app.push("latest")
  }
}
