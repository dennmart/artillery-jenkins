pipeline {
    agent {
        docker {
            image 'artilleryio/artillery:latest'
            args '-u root:root -i --entrypoint='
        }
    }

    stages {
        stage('Load Test') {
            steps {
                checkout scm
                sh 'mkdir reports'
                sh '/home/node/artillery/bin/artillery run --output reports/report.json tests/performance/socket-io.yml'
                sh '/home/node/artillery/bin/artillery report --output reports/report.html reports/report.json'
            }
        }
    }

    post {
        success {
            archiveArtifacts 'reports/*'
        }
    }
}
