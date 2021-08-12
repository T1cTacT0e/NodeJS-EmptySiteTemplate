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

    stage('Test') {
      steps {
        sh '''node server.js &
 sleep 5 &&
curl localhost:8081
if [[ "x$?" == "x0" ]]; 
then    echo good; 
else exit 1; 
fi
'''
      }
    }

  }
}