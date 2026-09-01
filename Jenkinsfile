pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out To-Do List App...'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build React Application') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy Build') {
            steps {
                bat 'if not exist "%JENKINS_HOME%\\userContent\\todo-list-app" mkdir "%JENKINS_HOME%\\userContent\\todo-list-app"'
                bat 'xcopy /E /I /Y dist "%JENKINS_HOME%\\userContent\\todo-list-app"'
            }
        }
    }

    post {
        success {
            echo 'To-Do List App deployed successfully!'
        }

        failure {
            echo 'Build failed. Check the console output.'
        }
    }
}