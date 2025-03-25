pipeline {
    agent {
        docker {
            image 'python:3.11'
        }
    }

   

    stages {

        stage('Compile project') {
            steps {
                sh "pip install -r requirements.txt"
                sh "pip list"
            }
        }

    }
    
}