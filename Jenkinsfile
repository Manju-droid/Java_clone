pipeline{
    agent any
        stages{
               stage("Deploy to client EC2"){
                 steps{
                       sshagent(['client-ec2-ssh']){
                       sh '''
                        ssh -o strictHostKeyChecking=no ubuntu@10.1.1.106 '
                        rm -rf project-2 || true &&
                        git clone https://github.com/Manju-droid/Java_clone.git project-2 || true &&
                        cd project-2  &&
                        docker stop container-1 || true &&
                        docker rm container-1 || true &&
                        docker build -t image-1 . &&
                        docker run -dit --name container-1 -p 8080:8080 image-1
                        '
                        '''
                       }
               }
           }    
    }
}
