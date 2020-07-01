pipeline {
  agent any
  stages {
    stage('stage1') {
      agent any
      steps {
        sh 'echo $HOSTNAME'
      }
    }

    stage('stage2') {
      agent any
      steps {
        sh 'echo $HOSTNAME'
      }
    }

  }
}