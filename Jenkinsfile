node {
     stage('Clone repository') {
         checkout scm
     }
     stage('Build image') {
         app = docker.build("mars-dkt/flask-example")
     }
     stage('Push image') {
         docker.withRegistry('https://asia-northeast3.gcr.io', 'gcr:[credentials-id]') {
             app.push("${env.BUILD_NUMBER}")
             app.push("latest")
         }
     }
}

stage('Build image') {
  app = docker.build("mars-dkt/flask-example")
}

stage('Push image') {
  docker.withRegistry('https://asia-northeast3.gcr.io', 'gcr:[credentials-id]')
  {
     app.push("${env.BUILD_NUMBER}")
     app.push("latest")
  }
}
