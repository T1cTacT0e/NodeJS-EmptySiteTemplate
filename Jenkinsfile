pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/T1cTacT0e/NodeJS-EmptySiteTemplate.git', changelog: true, poll: true, branch: 'master')
      }
    }

    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

  }
}