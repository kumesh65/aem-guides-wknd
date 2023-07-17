pipeline {
    agent any

    stages {
        stage("A") {
            options {
                timeout(time: 3, unit: "SECONDS")
            }

            steps {
                script {
                    Exception caughtException = null
                     def userInput = input 'Do you approve pub1 deployment?'
                     echo "value is, $userInput"
                    catchError(buildResult: 'SUCCESS', stageResult: 'ABORTED') { 
                        try { 
                            echo "Started stage A"
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
            }
        }
    }
}
