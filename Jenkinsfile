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
      parallel {
        stage('Author') {
          steps {
            echo 'I start to deployment to author.'
          }
        }

        stage('Publisher 1') {
          steps {
            input(message: 'Do you approve pub1 deployment?', id: 'pub-01-id-cnfrm', ok: 'Confirm')
            echo 'I am deploying to pub1.'
          }
        }

        stage('Publisher2') {
          steps {
            input(message: 'Do you approve pub 2deployment?', id: 'pub-02-id-cnfrm', ok: 'Confirm')
            echo 'I am deploying to pub2.'
          }
        }

      }
    }

    stage('Dispatcher Cache Flush') {
      steps {
        echo 'I am clearing cache from dispatcher one.'
      }
    }

    stage('Inform') {
      steps {
        echo 'Will innform the QA team for sanity.'
      }
    }

    stage('End') {
      steps {
        echo 'I am done...!'
      }
    }

  }
  tools {
    maven 'maven-383'
  }
}