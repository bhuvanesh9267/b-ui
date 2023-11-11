pipeline{
    agent any
    stages{
        stage('build image'){
            steps{
                sh "docker build -t bhuviecr ."
            }
        }

        // stage('tag image'){
        //     steps{
        //         sh "docker tag bhuviecr:latest 837016921632.dkr.ecr.ap-south-1.amazonaws.com/bhuviecr:1.2"
        //     }
        // }

        // stage('aws ecr configure'){
        //     steps{
        //         sh "aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 837016921632.dkr.ecr.ap-south-1.amazonaws.com"
        //     }
        // }

        // stage('push image'){
        //     steps{
        //         sh "docker push 837016921632.dkr.ecr.ap-south-1.amazonaws.com/bhuviecr:1.2"
        //     }
        // }

        // stage('store image value to ssm'){
        //     steps{
        //         sh "aws ssm put-parameter --name /ECR/bhuviecr --value 837016921632.dkr.ecr.ap-south-1.amazonaws.com/bhuviecr:1.2 --type String --region ap-south-1 --overwrite"
        //     }
        // }

        // stage('push image to docker hub'){
        //     steps{
        //         sh "sudo docker push bhuvaneshs512/myimage5:1.1"
        //     }
        // }
            
    }
}
