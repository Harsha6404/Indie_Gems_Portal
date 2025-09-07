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
        sh 'docker rmi -f game || true'
        sh 'docker build -t game .'
    }
}
        stage('Push to Docker Hub') {
    steps {
      withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', passwordVariable: 'passwd', usernameVariable: 'user')]) {
           
         sh 'echo "$passwd" | docker login -u $user --password-stdin' 
   sh 'docker tag game $user/game:v1'
   sh 'docker push $user/game:v1'
}
}

stage('container') {
    steps {
        sh 'docker rm -f game1 || true'
        sh 'docker run -itd --name game1 -p 81:80 game'
    }
}

    }
}
