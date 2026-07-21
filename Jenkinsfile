pipeline {
    agent any

    stages {
        stage('Restore') {
            when {
                branch 'main'
            }
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build') {
            when {
                branch 'main'
            }
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Test') {
            when {
                branch 'main'
            }
            steps {
                sh 'dotnet test --no-build'
            }
        }
    }

        post {
            success {
                echo 'all tests passed successfully!'
            }
            failure {
                echo 'Check logs for build or test errors.'
            }
        }
}
