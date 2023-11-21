pipeline {
    agent any
    parameters { (name: '933060838752.dkr.ecr.eu-central-1.amazonaws.com/jenkins_agent', defaultValue:'',description: '')}
    string(name: '933060838752.dkr.ecr.eu-central-1.amazonaws.com/jenkins_agent', value: '$ECR_URL/$IMAGE_NAME:$BUILD_NUMBER')
    stages {
        stage('Deploy') {
                steps {

                sh '''
                # kubectl apply -f aaa.yaml

                '''
                }
            }

    }
}