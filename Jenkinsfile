pipeline {
    agent any

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
