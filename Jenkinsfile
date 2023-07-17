pipeline {
    agent any

    stages {
        stage("A") {

            steps {
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

        stage("B") {
            steps {
                echo "Started stage B"
                script {
                    Exception caughtException = null

                    catchError(buildResult: 'SUCCESS', stageResult: 'ABORTED') { 
                        try { 
                            echo "Started stage B"
                            input 'Do you approve pub2 deployment?'
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
