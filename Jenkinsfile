pipeline{
    agent any
    stages{
        stage("Build Image"){
            steps{
                script{
                    dockerapp = docker.build("danilompr/apiproductk8s:${env.BUILD_ID}","-f ./ProductAPI/Dockerfile .")
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
            stage("Deploy Kubernetes"){
                environment{
                    tag_verison = "${env.BUILD_ID}"
                }
                steps{
                    withKubeConfig([credentialsId:"kubeconfig"]){
                        bat "sed -i 's/{{tag}}/tag-version/g' /apiproduct.yaml"
                        bat "kubectl apply -f apiproduct.yaml"
                    }
                }

            }
    }
}
