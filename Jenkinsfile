pipeline {
    agent {
        label "master"
    }
    stages {
        stage("Invoking docker build") {
            steps {
                sh "docker build -t localhost:5000/bitlbee-libpurple:latest ."
            }
        }
        stage("Invoking docker push") {
            steps {
                sh "docker push localhost:5000/bitlbee-libpurple:latest"
            }
        }
    }
    post {
        always {
            sendNotifications currentBuild.result
        }
    }
}
