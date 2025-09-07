pipeline {
    agent any 
    stages {
      stage('Checkout Code') {
    steps {
        git branch: 'main', url: 'https://github.com/Harsha6404/Indie_Gems_Portal.git'
    }
}

       stage('Install & Clean') {
    steps {
        sh 'npm run clean || echo "No clean script, skipping"'
        sh 'npm install'
        sh 'npm run build'
    }
}
       stage('docker_image') {
           steps {
               sh 'rmi -rf game || true '
               sh 'docker build -t game .'
           }
       }
        stage('container') {
            steps {
                sh 'rm -f game1 || true'
                sh 'docker run -itd --name game1 -p 81:80 game'
            }
        }
    }
}
