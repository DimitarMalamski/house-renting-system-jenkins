pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Check .NET SDK') {
            steps {
                bat '''
                dotnet --version
                dotnet --info
                '''
            }
        }

        stage('Restore') {
            steps {
                bat '''
                dotnet restore
                '''
            }
        }

        stage('Build') {
            steps {
                bat '''
                dotnet build --configuration Release --no-restore
                '''
            }
        }

        stage('Test') {
            steps {
                bat '''
                dotnet test --configuration Release --no-build
                '''
            }
        }
    }
}