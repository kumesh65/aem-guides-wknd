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
            input(message: 'Author deployment', id: 'auth-dep', ok: 'Yes')
          }
        }

        stage('Publisher 1') {
          steps {
            input(message: 'Please approve Pub one deployment', id: 'pub-01-dep', ok: 'Yes')
          }
        }

        stage('Publisher 2') {
          steps {
            input(message: 'Please approve pub2 deployment', id: 'pub-02-dep', ok: 'Yes')
          }
        }

        stage('Publisher 3') {
          steps {
            input(message: 'Please approve pub 03 deployment', id: 'pub-03-dep', ok: 'Yes')
          }
        }

        stage('Publisher 4') {
          steps {
            input(message: 'Please approve pub 04 deployment', id: 'pub-04-dep', ok: 'Yes')
          }
        }

      }
    }

    stage('Dispatcher Cache flush') {
      steps {
        echo 'We are about the flush the dispatcher cache.'
      }
    }

    stage('Notify QA') {
      steps {
        echo 'Production deployment done please do smoke testing'
      }
    }

    stage('End') {
      steps {
        echo 'Release completed..!'
      }
    }

  }
  tools {
    maven 'maven-383'
  }
}