pipeline {
    agent {
        docker { image 'artilleryio/artillery:latest' }
    }
    stages {
        stage('Load Test') {
            steps {
                checkout scm
                sh '/home/node/artillery/bin/artillery run tests/performance/socket-io.yml'
            }
        }
    }
}
