node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
        echo 'Building Docker image...'
        app = docker.build("ivica650/jenkins_homework")
    }
    stage('Push image') {
        echo 'Pushing image to Docker Hub...'
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
        }
    }
}