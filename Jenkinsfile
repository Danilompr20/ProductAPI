pipeline{
    agent any
    stages{
        stage("Build Image"){
            steps{
                script{
                    dockerapp = docker.build("danilompr/apiproductK8S:${env.BUILD_ID}","-f ./ProductAPI/Dockerfile .")
                }
               
            }
          
        }
        stage("Push Image"){
                steps{
                    script{
                        docker.withRegistry("https://registry.hub.docker.com", "dockerhub"){
                            dockerapp.push("latest")
                            dockerapp.push("${env.BUILD_ID}")
                        }
                        
                    }
                }
            }
    }
}
