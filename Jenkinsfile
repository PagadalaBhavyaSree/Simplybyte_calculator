pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                bat 'docker build -t calculator-app .'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                docker stop calculator-container 2>NUL
                docker rm calculator-container 2>NUL
                docker run -d -p 5000:5000 --name calculator-container calculator-app
                '''
            }
        }
    }
}