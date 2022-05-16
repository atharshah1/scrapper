pipeline{
    environment{
        IMAGE_NAME="mohammadathar/scraper"
        dockerImage=''
        DOCKER_C='docker_credentials'
    }
    agent any
    stages{
        stage('Building Image'){
            steps{
                // using docker pipeline plugin
                script{
                     dockerImage = docker.build env.IMAGE_NAME

                }
            }
        }
        stage('pushing image to dockerhub'){
            steps{
                script{   
                docker.withRegistry('', env.DOCKER_C){
                    dockerImage.push()
                    }
                }
            }
        }
        stage('Deploy to K8s')
  {
   steps{
    sshagent(['k8s-jenkins'])
    {
     sh 'scp -r -o StrictHostKeyChecking=no scraper-deployment.yml ubuntu@3.89.164.172:/home/ubuntu/'
script{
      try{
       sh 'ssh ubuntu@3.89.164.172 kubectl apply -f /home/ubuntu/scraper-deployment.yml --kubeconfig=/home/ubuntu/.kube/config'
}catch(error)
       {
}
     }
    }
   }
  }
    }
}
