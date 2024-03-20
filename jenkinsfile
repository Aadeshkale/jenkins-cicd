node {

    stage('checkout') {
    git branch: 'main', url: 'https://github.com/Aadeshkale/jenkins-cicd.git'
    sh 'echo "code pulled.."'
    }

    stage('build image') {
    sh 'cd web-app'
    docker.build "web-app:${env.BUILD_ID}"    
    }
    
    
}