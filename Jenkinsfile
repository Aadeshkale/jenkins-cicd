pipeline {

    agent any

    stages {
        
        stage('checkout') {

            steps{
                git branch: 'main', url: 'https://github.com/Aadeshkale/jenkins-cicd.git'
                sh 'echo "code pulled.."'
                sh 'echo ${env.GIT_BRANCH}'
                sh 'printenv | sort'
            }
        }

                                                 
        stage('build image') {
            
              steps{
                    script{
                        if ( env.GIT_BRANCH == "origin/main") { 
                            sh "echo inside if"
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
                        else {
                            sh "echo inside else block"
                        }
                
                    }
                }

            

        }
        
    }    
    // execute always at end of pipeline
    post { 
        always { 
            cleanWs()
            sh "docker system prune -a -f"
        }
    }

    
}