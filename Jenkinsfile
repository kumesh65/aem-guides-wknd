pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'I am building your code..!'
            }
        }

        stage('Install') {
            parallel {
                stage('Author') {
                    steps {
                        script {
                            try {
                                def restartStep = false

                                // Step 1 logic
                                input message: 'Proceed with Author deployment? (Click "Proceed" to continue or "Abort" to restart)', ok: 'Proceed'

                                if (env.RESTART_STEP == 'Yes') {
                                    restartStep = true
                                    echo 'Restarting Step 1...'
                                }

                                // Your Step 1 code here

                                if (restartStep) {
                                    error('Author was restarted')
                                }
                            } catch (Exception e) {
                                error("Author failed: ${e.message}")
                            }
                        }
                    }
                }

                stage('Publish 1') {
                    steps {
                        script {
                            try {
                                def restartStep = false

                                // Step 2 logic
                                input message: 'Proceed with Publish 1? (Click "Proceed" to continue or "Abort" to restart)', ok: 'Proceed'

                                if (env.RESTART_STEP == 'Yes') {
                                    restartStep = true
                                    echo 'Restarting Step 2...'
                                }

                                // Your Step 2 code here

                                if (restartStep) {
                                    error('Publish 1 was restarted')
                                }
                            } catch (Exception e) {
                                error("Publish 1 failed: ${e.message}")
                            }
                        }
                    }
                }
                stage('Publish 2') {
                    steps {
                        script {
                            try {
                                def restartStep = false

                                // Step 2 logic
                                input message: 'Proceed with Publish 2? (Click "Proceed" to continue or "Abort" to restart)', ok: 'Proceed'

                                if (env.RESTART_STEP == 'Yes') {
                                    restartStep = true
                                    echo 'Restarting Publish 2...'
                                }

                                // Your Step 2 code here

                                if (restartStep) {
                                    error('Publish 2 was restarted')
                                }
                            } catch (Exception e) {
                                error("Publish 2 failed: ${e.message}")
                            }
                        }
                    }
                }

                // Include similar logic for other parallel steps (Step 3, Step 4, etc.)
            }
        }

        // Add more stages as needed
         stage('Dispatcher Cache Flush') {
            steps {
                    echo 'I am clearing cache from dispatcher one.'
                }
        }
    }

    // Add post actions or notifications as needed
    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
