pipeline {
    agent {
        docker {
            image 'ppodgorsek/robot-framework'
        }
    }

    stages {
        stage('Install python'){
                steps {
                sh'pip freeze > requirements.txt'
                sh ' python3 -m pip install -r requirements.txt'
            }
        }
    
        stage('Run Selenium Tests') {
            steps {
                // Exécution des tests avec Selenium
                sh  'python3 -m robot tests/test_temp.robot'
            }
        }
        stage('Publish Robot Reports') {
            steps {
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'results',
                    reportFiles: 'log.html',
                    reportName: 'Robot Framework Report'
                ])
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'results/*', fingerprint: true
        }
    }

}