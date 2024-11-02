node {
    docker.image('python:3.8').inside {
        stage("Build & Test") {
            try {
                sh "echo Running Build and Test"
                sh "ls -la"
                sh "python3 ./sources/test_calc.py"
            } catch (Exception e) {
                echo "Error occurred during Build & Test: ${e.getMessage()}"
                error("Build & Test stage failed.")
            }
        }

        stage("Deploy") {
            input {
                message "Lanjut deploy app?"
                ok "Deploy"
            }
            sh "python3 ./sources/calc.py"
            echo "Wait 1 Minutes"
            sleep(time: 1, unit: "MINUTES")
        }
    }
}