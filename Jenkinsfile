pipeline {
  agent any
  tools { 
        maven 'maven-383' 
    }
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
            input 'Do you approve pub1 deployment?'
            echo 'I am deploying to pub1.'
          }
        }

        stage('Publisher2') {
          steps {
            input 'Do you approve pub 2deployment?'
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
}
