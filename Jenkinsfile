pipeline{
    agent any

    environment {
        IMAGE_NAME = 'front-end'
        CONTAINER_NAME = 'front-end-container'
    }

    stages{
        stage("Clone Repository") {
            steps{
                checkout scm
            }
        }

        stage("Build Docker Image") {
            steps {
                script {
                    sh "docker build -t ${IMAGE_NAME} ."
                } 
            }
        }

        stage("Run Tests") {
            steps {
                sh "docker run -it --rm ${IMAGE_NAME} npm run start:dev"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
