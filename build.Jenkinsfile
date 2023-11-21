pipeline {
    agent {
    docker {
        image '<docker-img>'
        args  '--user root -v /var/run/docker.sock:/var/run/docker.sock'
    }
}

    environment {
        ECR_URL = '933060838752.dkr.ecr.eu-central-1.amazonaws.com'
        IMAGE_NAME = 'roberta-jenkins'
    }

    stages {
        stage('Build') {
                steps {
                sh '''
                aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin $ECR_URL
                docker build -t $IMAGE_NAME:$BUILD_NUMBER .
                docker tag $IMAGE_NAME:$BUILD_NUMBER $ECR_URL/$IMAGE_NAME:$BUILD_NUMBER
                docker push $ECR_URL/$IMAGE_NAME:$BUILD_NUMBER
                '''
                }
            }
        stage('Trigger Deploy') {
                steps {
                sh '#if we put wait true then the build will wait until the deploy will finish'
                build job: 'RobertaDeploy', wait: false, parameters: [
                    string(name: 'ROBERTA_IMAGE_URL', value: '$ECR_URL/$IMAGE_NAME:$BUILD_NUMBER')
                ]
                }
            }

    }
}