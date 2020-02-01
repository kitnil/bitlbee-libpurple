pipeline {
    agent {
        label "master"
    }
    stages {
        stage("Invoking Docker") {
            steps {
                script {
                    docker.withRegistry('http://localhost:5000') {
                        customImage = docker.build("bitlbee-libpurple:${env.BUILD_ID}")
                        customImage.push()
                        customImage.push('latest')
                    }
                }
            }
        }
    }
    post {
        always {
            sendNotifications currentBuild.result
        }
    }
}
