pipeline {
    agent any

    branches {
        only 'main'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore Dependencies') {
            steps {
                echo 'Restoring NuGet packages...'
                sh "dotnet restore "
            }
        }

        stage('Build') {
            steps {
                echo 'Building .NET solution'
                sh "dotnet build --no-restore"
            }
        }

        stage('Test') {
            steps {
                echo 'Executing test projects...'
                sh "dotnet test"
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