node {

    stage('Checkout') {
        checkout scm
    }

    stage('Build Frontend Image') {
        sh 'docker build -t vivekbhardwaj581/flipkart-frontend:v1.7 ./frontend'
    }

    stage('Build Backend Image') {
        sh 'docker build -t vivekbhardwaj581/flipkart-backend:v1.7 -f Dockerfile.backend .'
    }

  stage("Docker Login") {

        withCredentials([string(credentialsId: 'dockerhubpassword', variable: 'dockerhubpassword')]) {

            sh "docker login -u vivekbhardwaj581 -p ${dockerhubpassword}"

        }
    }



    stage('Push Images') {
        sh 'docker push vivekbhardwaj581/flipkart-frontend:v1.7'
        sh 'docker push vivekbhardwaj581/flipkart-backend:v1.7'
    }

    stage('Remove Old Containers') {
        sh 'docker rm -f frontend backend || true'
    }

    stage('Deploy Backend') {
        sh '''
        docker run -d \
          --name backend \
          --link mongodb:mongodb \
          -p 4000:4000 \
          vivekbhardwaj581/flipkart-backend:v1.7
        '''
    }

    stage('Deploy Frontend') {
        sh '''
        docker run -d \
          --name frontend \
          -p 8000:80 \
          vivekbhardwaj581/flipkart-frontend:v1.7
        '''
    }

    stage('Verify Deployment') {
        sh 'docker ps'
    }
}
