pipeline {
    agent any

    stage('checkout') {
        git branch: 'main', url: 'https://github.com/Aadeshkale/jenkins-cicd.git'
        sh 'echo "code pulled.."'
    }

    stage('build image') {

        sh "pwd"
        // This step need to add jenkins user to docker diamon permission
        //   sudo usermod -a -G docker jenkins
        
        docker.build ("web-app:${env.BUILD_ID}", "./web-app")
        // Alternative way for change dir
        // dir("${env.WORKSPACE}/web-app"){
        //     script{
        //         docker.build "web-app:${env.BUILD_ID}"
        //     }
        // }

    }
    stage('cleaning') {
        sh "docker system prune -a -f"
    }
    
}