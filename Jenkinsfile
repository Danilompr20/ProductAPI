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
    }
}
