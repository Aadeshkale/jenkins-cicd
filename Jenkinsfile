node {

    stage('checkout') {
    git branch: 'main', url: 'https://github.com/Aadeshkale/jenkins-cicd.git'
    sh 'echo "code pulled.."'
    }

    stage('build image') {
    dir("${env.WORKSPACE}/web-app"){
        sh "pwd"
    }    
    sh 'ls -la'
    docker.build "web-app:${env.BUILD_ID}"    
    }
    
    
}