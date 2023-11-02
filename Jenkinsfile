pipeline{
    agent any
    stages{
        stage('describe repositories'){
            steps{
                sh "aws ecr describe-repositories --region 'ap-south-1'"
            }
        }

        stage('clone repo'){
            steps{
                git credentialsId: "github", url:'https://github.com/bhuvanesh9267/b-ui'
            }
            
        }

        stage('build image'){
            steps{
                sh "docker build -t bhuviecr ."
            }
        }

        stage('tag image'){
            steps{
                sh "docker tag bhuviecr:latest 837016921632.dkr.ecr.ap-south-1.amazonaws.com/bhuviecr:latest"
            }
        }

        stage('aws ecr configure'){
            steps{
                sh "aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 837016921632.dkr.ecr.ap-south-1.amazonaws.com"
            }
        }

        stage('push image'){
            steps{
                sh "docker push 837016921632.dkr.ecr.ap-south-1.amazonaws.com/bhuviecr:latest"
            }
        }

        stage('store image value to ssm'){
            steps{
                sh "aws ssm put-parameter --name ECR/bhuviecr --value 837016921632.dkr.ecr.ap-south-1.amazonaws.com/bhuviecr:latest --type String --region ap-south-1 --overwrite"
            }
        }
    }
}
