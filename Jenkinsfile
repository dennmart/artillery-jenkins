pipeline {
    stages {
        stage('Checkout repo') {
            steps {
                checkout scm
            }
        }

        stage('Run Artillery load test') {
            agent {
                docker {
                    image 'artilleryio/artillery:latest'
                    args '-i --entrypoint='
                }
            }

            steps {
                sh '/home/node/artillery/bin/artillery run tests/performance/socket-io.yml'
            }
        }
    }
}
