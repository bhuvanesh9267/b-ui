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
                sh "docker build -t bhuvirepo ."
            }
        }

        stage('tag image'){
            steps{
                sh "docker tag bhuvirepo:latest 837016921632.dkr.ecr.ap-south-1.amazonaws.com/bhuvirepo:latest"
            }
        }

        stage('aws ecr configure'){
            steps{
                sh "aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 837016921632.dkr.ecr.ap-south-1.amazonaws.com"
            }
        }

        stage('push image'){
            steps{
                sh "docker push 837016921632.dkr.ecr.ap-south-1.amazonaws.com/bhuvirepo:latest"
            }
        }
    }
}