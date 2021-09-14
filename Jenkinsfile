pipeline {
    agent {
        docker {
            image 'artilleryio/artillery:latest'
            args '-i --entrypoint='
        }
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
