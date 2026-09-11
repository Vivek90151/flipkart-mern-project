
node {

    stage('Checkout') {
        checkout scm
    }

    stage('Build Frontend Image') {
        sh 'docker build -t flipkart-frontend:v1.7 ./frontend'
    }

    stage('Build Backend Image') {
        sh 'docker build -t flipkart-backend:v1.7 -f Dockerfile.backend .'
    }

    stage('Check Images') {
        sh 'docker images | grep flipkart'
    }
}

