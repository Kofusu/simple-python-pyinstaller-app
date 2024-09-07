node {
    docker.image('python:3.8').inside {
        stage("Build & Test") {
            try {
                sh "echo Running Build and Test"
                sh "python3 sources/test_calc.py"
            } catch (Exception e) {
                echo "Error occurred during Build & Test: ${e.getMessage()}"
                error("Build & Test stage failed.")
            }
        }

        stage("Deploy") {
            sh "echo Not yet Implemented"
            sh "pwd"
        }
    }
}