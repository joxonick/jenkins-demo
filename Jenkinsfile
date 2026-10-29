pipeline {
    agent any

        triggers {
        pollSCM('H/5 * * * *')        // check Git every ~5 minutes; build only if there are new commits
        cron('H 8 * * 1-5')           // also build every weekday around 08:00
    }

    stages {
        stage('Checkout info') {
            steps {
                echo "Branch: ${env.GIT_BRANCH}, commit: ${env.GIT_COMMIT}"
            }
        }
        stage('Run app') {
            steps {
                bat 'python app.py'        // Linux/Docker: sh 'python3 app.py'
            }
        }
        stage('Test') {
            steps {
                bat 'python -m unittest -v' // Linux/Docker: sh 'python3 -m unittest -v'
            }
        }
    }
}
