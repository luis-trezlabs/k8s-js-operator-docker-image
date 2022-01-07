pipeline {
  agent any
  stages {
    stage('Build Image') {
      steps {
        sh 'docker build . -t luisbodev/js-operator-test'
      }
    }

  }
}