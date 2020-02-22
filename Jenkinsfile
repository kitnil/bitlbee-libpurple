pipeline {
    agent {
        label "master"
    }
    stages {
        stage("Invoking Docker") {
            steps {
                sh "docker build -t localhost:5000/bitlbee-libpurple:latest ."
            }
        }
        stage("Deploy") {
            steps {
                sh "docker save localhost:5000/bitlbee-libpurple:latest | bzip2 | ssh oracle 'bunzip2 | docker load'"
            }
        }
    }
    post {
        always {
            sendNotifications currentBuild.result
        }
    }
}
