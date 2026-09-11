node {

    stage('Checkout') {
        checkout scm
    }

    stage('Debug') {
        sh 'pwd'
        sh 'ls -la'
        sh 'ls -la frontend'
        sh 'ls -la backend'
    }

    stage('Build Frontend Image') {
        sh 'docker build -t flipkart-frontend:v1.7 ./frontend'
    }

    stage('Build Backend Image') {
        sh 'docker build -t flipkart-backend:v1.7 ./backend'
    }
}
