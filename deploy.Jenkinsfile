pipeline {
    agent any
    parameters { string(name: 'ROBERTA_IMAGE_URL', defaultValue:'',description: '')}
    string(name: 'ROBERTA_IMAGE_URL', value: '$ECR_URL/$IMAGE_NAME:$BUILD_NUMBER')
    stages {
        stage('Deploy') {
                steps {

                sh '# kubectl apply -f aaa.yaml''
                }
            }

    }
}