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
'''
      }
    }

    stage('Package Code') {
      steps {
        sh 'tar -czvf node.tar.gz  .'
      }
    }

    stage('Publish the archive') {
      steps {
        archiveArtifacts 'node.tar.gz'
        cleanWs(cleanWhenAborted: true, cleanWhenFailure: true, cleanWhenNotBuilt: true, cleanWhenSuccess: true, cleanWhenUnstable: true, deleteDirs: true, cleanupMatrixParent: true, disableDeferredWipeout: true)
      }
    }

  }
}