pipeline {
  agent {
    node {
      label 'Build'
    }

  }
  stages {
    stage('Build Image') {
      steps {
        sh 'build .'
      }
    }

  }
}