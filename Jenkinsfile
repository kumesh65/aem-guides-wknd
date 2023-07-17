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
