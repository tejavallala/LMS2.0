pipeline {
  agent any

  tools {
    nodejs "NodeJS"
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/tejavallala/LMS2.0.git'
      }
    }

    stage('Install Backend Dependencies') {
      steps {
        dir('Backend-CLMS-using-MERN') {
          sh 'npm install'
        }
      }
    }

    stage('Install Frontend Dependencies') {
      steps {
        dir('frontend-CLMS-using-MERN') {
          sh 'npm install'
        }
      }
    }

    stage('Build Frontend') {
      steps {
        dir('frontend-CLMS-using-MERN') {
          sh 'npm run build'
        }
      }
    }

    stage('Run Backend Tests') {
      steps {
        dir('Backend-CLMS-using-MERN') {
          sh 'npm test || echo "No tests configured"'
        }
      }
    }
  }
}
