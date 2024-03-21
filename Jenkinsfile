pipeline {

    environment {
        FULL_PATH_BRANCH = "${sh(script:'git name-rev --name-only HEAD', returnStdout: true)}"
        BRANCH_NAME = FULL_PATH_BRANCH.substring(FULL_PATH_BRANCH.lastIndexOf('/') + 1, FULL_PATH_BRANCH.length())
        ALREADY_EXISTS = "true"
    }

    agent any

    stages {
        
        stage('checkout') {

            steps{
                git branch: 'main', url: 'https://github.com/Aadeshkale/jenkins-cicd.git'
                sh 'echo "code pulled.."'
            }
        }

                                                 
        stage('build image') {
            
              steps{
                    script{
                        sh "echo ${env.BRANCH_NAME}"

                        if ( ALREADY_EXISTS == "true") { 
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
    // post { 
    //     always { 
    //         cleanWs()
    //         sh "docker system prune -a -f"
    //     }
    // }

    
}