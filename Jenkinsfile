node {
    stage("Checkout") {
        checkout scm  // Mengambil kode dari repositori yang terkonfigurasi di Jenkins
    }

    docker.image('python:3.8').inside {
        stage("Build") {
            try {
                sh "echo Running Build"
            } catch (Exception e) {
                echo "Error occurred during Build & Test: ${e.getMessage()}"
                error("Build & Test stage failed.")
            }
        }

        stage("Test") {
            try {
                sh "echo Running Test"
                sh "python3 sources/test_calc.py"
            } catch (Exception e) {
                echo "Error occurred during Build & Test: ${e.getMessage()}"
                error("Build & Test stage failed.")
            }
        }

        stage("Manual Approval") {
            input message: "Lanjutkan ke tahap Deploy?", ok: "Deploy"
        }

        stage("Deploy") {
            echo "Wait 1 Minutes"
            sleep(time: 1, unit: "MINUTES")
            sh "sources/calc.py"
        }
    }
}
