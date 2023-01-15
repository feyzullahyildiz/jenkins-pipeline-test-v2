pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t feyzullahyildiz/test-nodejsapp:${BUILD_NUMBER} ./nodejs'
                sh 'docker tag feyzullahyildiz/test-nodejsapp:${BUILD_NUMBER} feyzullahyildiz/test-nodejsapp:latest'
            }
        }
        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker_hub_credentials', passwordVariable: 'DOCKER_HUB_PASSWORD', usernameVariable: 'DOCKER_HUB_USERNAME')]) {
                    sh 'docker login -u $DOCKER_HUB_USERNAME -p $DOCKER_HUB_PASSWORD'
                    sh 'docker push feyzullahyildiz/test-nodejsapp:${BUILD_NUMBER}'
                    sh 'docker push feyzullahyildiz/test-nodejsapp:latest'
                }
            }
        }
    }
}
