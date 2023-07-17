pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'I am building your code..!'
        sh '''#!/bin/bash
        echo $PWD
        mvn clean install'''
        archiveArtifacts artifacts: 'ui.apps.structure/target/*.zip, ui.content/target/*.zip, all/target/juniper.all-2.10.0-SNAPSHOT.zip',
            fingerprint: true,
            onlyIfSuccessful: true
      }
    }

    stage('Author') {
      parallel {
        stage('Author') {
          steps {
            echo 'I start to deployment to author.'
            script {
                    Exception caughtException = null

                    catchError(buildResult: 'SUCCESS', stageResult: 'ABORTED') { 
                        try { 
                            echo "Started stage A"
                            input 'Do you approve pub1 deployment?'
                        } catch (org.jenkinsci.plugins.workflow.steps.FlowInterruptedException e) {
                            error "Caught ${e.toString()}" 
                        } catch (Throwable e) {
                            caughtException = e
                        }
                    }

                    if (caughtException) {
                        error caughtException.message
                    }
                }
          }
        }

        stage('Publisher 1') {
          steps {
            input 'Do you approve pub1 deployment?'
            echo 'I am deploying to pub1.'
           script {
                    Exception caughtException = null

                    catchError(buildResult: 'SUCCESS', stageResult: 'ABORTED') { 
                        try { 
                            echo "Started stage A"
                            input 'Do you approve pub1 deployment?'
                        } catch (org.jenkinsci.plugins.workflow.steps.FlowInterruptedException e) {
                            error "Caught ${e.toString()}" 
                        } catch (Throwable e) {
                            caughtException = e
                        }
                    }

                    if (caughtException) {
                        error caughtException.message
                    }
                }
          }
        }

        stage('Publisher2') {
          steps {
            input 'Do you approve pub 2deployment?'
            echo 'I am deploying to pub2.'
            script {
                    Exception caughtException = null

                    catchError(buildResult: 'SUCCESS', stageResult: 'ABORTED') { 
                        try { 
                            echo "Started stage A"
                            input 'Do you approve pub1 deployment?'
                        } catch (org.jenkinsci.plugins.workflow.steps.FlowInterruptedException e) {
                            error "Caught ${e.toString()}" 
                        } catch (Throwable e) {
                            caughtException = e
                        }
                    }

                    if (caughtException) {
                        error caughtException.message
                    }
                }
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
