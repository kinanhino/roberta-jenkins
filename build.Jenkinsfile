pipeline {
    agent any

    stages {
        stage('Build') {
                steps {
                sh '''
                aws ecr get-login-password --region eu-central-1 | docker login --username AWS --password-stdin 933060838752.dkr.ecr.eu-central-1.amazonaws.com
                docker build -t roberta-jenkins .
                docker tag kinan-jen-roberta:latest 933060838752.dkr.ecr.eu-central-1.amazonaws.com/kinan-jen-roberta:latest
                docker push 933060838752.dkr.ecr.eu-central-1.amazonaws.com/kinan-jen-roberta:latest
                '''
                }
            }

    }
}