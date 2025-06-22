pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                git branch: 'main', url: 'https://github.com/Gabriel-Gianvechio/jenkins-public-github.git'
            }
        }
        
        stage('Building Images') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        
        stage('Dploying application') {
            steps {
                sh '''
                    docker stop webapp_ctr || true
                    docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}
                '''
            }
        }
    }
}
