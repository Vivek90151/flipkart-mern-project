node {

    stage('Checkout') {
        checkout scm
    }

    stage('Debug') {
        sh '''
            echo "===== ROOT ====="
            pwd
            ls -la

            echo "===== FRONTEND ====="
            ls -la frontend

            echo "===== BACKEND ====="
            ls -la backend
        '''
    }

    stage('Build Frontend Image') {
        sh '''
            docker build \
            -t flipkart-frontend:v1.7 \
            ./frontend
        '''
    }

    stage('Build Backend Image') {
        sh '''
            docker build \
            -t flipkart-backend:v1.7 \
            .
        '''
    }

    stage('Docker Images') {
        sh '''
            docker images | grep flipkart
        '''
    }
}
