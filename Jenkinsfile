pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'I am building your code..!'
            }
        }

        stage('Parallel Steps') {
            parallel {
                stage('Step 1') {
                    steps {
                        script {
                            try {
                                def restartStep = false

                                // Step 1 logic
                                input message: 'Proceed with Step 1? (Click "Proceed" to continue or "Abort" to restart)', ok: 'Proceed'

                                if (env.RESTART_STEP == 'Yes') {
                                    restartStep = true
                                    echo 'Restarting Step 1...'
                                }

                                // Your Step 1 code here

                                if (restartStep) {
                                    error('Step 1 was restarted')
                                }
                            } catch (Exception e) {
                                error("Step 1 failed: ${e.message}")
                            }
                        }
                    }
                }

                stage('Step 2') {
                    steps {
                        script {
                            try {
                                def restartStep = false

                                // Step 2 logic
                                input message: 'Proceed with Step 2? (Click "Proceed" to continue or "Abort" to restart)', ok: 'Proceed'

                                if (env.RESTART_STEP == 'Yes') {
                                    restartStep = true
                                    echo 'Restarting Step 2...'
                                }

                                // Your Step 2 code here

                                if (restartStep) {
                                    error('Step 2 was restarted')
                                }
                            } catch (Exception e) {
                                error("Step 2 failed: ${e.message}")
                            }
                        }
                    }
                }

                // Include similar logic for other parallel steps (Step 3, Step 4, etc.)
            }
        }

        // Add more stages as needed
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
