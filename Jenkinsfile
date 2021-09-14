pipeline {
    agent {
        docker {
            image 'artilleryio/artillery:latest'
            args '-u root:root -i --entrypoint='
        }
    }

    triggers {
        cron('0 0 * * *')
    }

    stages {
        stage('Set up Artillery Pro') {
            steps {
                sh 'npm install -g artillery-pro@latest'
            }
        }
        stage('Load Test on AWS') {
            steps {
                sh '/home/node/artillery/bin/artillery version'
                // sh '/home/node/artillery/bin/artillery run-test --cluster artillery-pro-cluster --region us-east-1 --count 5'
            }
        }
    }
}
