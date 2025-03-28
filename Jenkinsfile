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
                    sh  'python3 -m robot -d test_results tests/test_temp.robot'
                }
        }
    }

    post {
      always {
                    // Note! Careful not to mix the Jenkins `robot` step with the `robot` command run inside the previous
                    // `sh` step! The `robot` step _only_ publishes the results for Jenkins and the `robot` command
                    // inside `sh` step runs the tests!
                    robot(
                        outputPath          : 'test_results',
                        outputFileName      : "output.xml",
                        reportFileName      : 'report.html',
                        logFileName         : 'log.html',
                        disableArchiveOutput: false,
                        passThreshold       : 95.0,
                        unstableThreshold   : 95.0,
                        otherFiles          : "**/*.png",
                    )
                }
    }
}