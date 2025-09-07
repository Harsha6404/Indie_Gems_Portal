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

    }
}
