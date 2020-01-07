pipeline {
    agent {
        label "master"
    }
    stages {
        stage("Invoking docker build") {
            steps {
                sh "docker build -t bitlbee-libpurple:latest ."
            }
        }
    }
    post {
        always {
            sendNotifications currentBuild.result
        }
    }
}
