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
    }
}
