pipeline {
    agent any

    stages {
        stage('List Successful Builds') {
            steps {
                script {
                    def successfulBuildNumbers = []
                    // Get the list of successful build numbers
                    def builds = Jenkins.instance.getItemByFullName('<your-job-name>').getBuilds().findAll { it.getResult().equals(hudson.model.Result.SUCCESS) }
                    builds.each { build ->
                        successfulBuildNumbers.add(build.getNumber().toString())
                    }

                    // Prompt the user to select a build number
                    def userInput = input(
                        id: 'buildNumber',
                        message: 'Select a successful build number:',
                        parameters: [
                            choice(
                                choices: successfulBuildNumbers,
                                description: 'Build Number'
                            )
                        ]
                    )

                    // Use the selected build number in subsequent stages
                    echo "Selected build number: ${userInput}"
                }
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
