pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'I am building your code..!'
        sh '''#!/bin/bash
        echo $PWD
        mvn clean install -DskipTests'''
      }
    }

    stage('Author') {
      steps {
        echo 'I start to deployment to author.'
      }
    }

    stage('Publisher 1') {
      steps {
        input(message: 'Do you want to deploy to publisher one?', id: 'id-pub1-confirm-message.', ok: 'Confirm')
      }
    }

    stage('Publisher 2') {
      steps {
        input(message: 'Do you want to deploy to publisher2?', id: 'id-pub2-confirm-message.', ok: 'Confirm')
      }
    }

    stage('Dispatcher Cache flush') {
      steps {
        echo 'We are about the flush the dispatcher cache.'
      }
    }

    stage('End') {
      steps {
        echo 'Your code deployed successfully.'
      }
    }

  }
  tools {
    maven 'maven-383'
  }
}