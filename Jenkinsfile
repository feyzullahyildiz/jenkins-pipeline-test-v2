pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t feyzullahyildiz/test-nodejsapp .'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker_hub_credentials', passwordVariable: 'DOCKER_HUB_PASSWORD', usernameVariable: 'DOCKER_HUB_USERNAME')]) {
                    sh 'docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_PASSWORD'
                    sh 'docker push feyzullahyildiz/test-nodejsapp'
                }
            }
        }
    }
}
