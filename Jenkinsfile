
node {

    stage('Checkout') {
        checkout scm
    }

    stage('Debug') {
        sh 'pwd'
        sh 'ls -la'
    }

    stage('Build Frontend Image') {
    steps {
        sh 'docker build -t flipkart-frontend:v1.7 ./frontend'
    }
}

stage('Build Backend Image') {
    steps {
        sh 'docker build -t flipkart-backend:v1.7 ./backend'
    }
}
