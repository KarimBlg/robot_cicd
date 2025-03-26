pipeline {
    agent {
        docker {
            image 'ppodgorsek/robot-framework'
        }
    }

   

    stages {

        stage('Compile project') {
            steps {
                sh"python3 -m venv venv"
                sh"source venv/bin/activate"

                //sh "pip freeze > requierements.txt"
                sh "pip3 install -r requirements.txt"
                sh "pip list"
            }
        }

    }
    
}