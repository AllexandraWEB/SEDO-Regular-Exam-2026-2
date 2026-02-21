pipeline {
    agent any

    stages {
        stage('Restore dependencies') {
            when {
                anyOf {
                    branch 'main'
                }
            }
            steps {
                sh 'dotnet restore'
            }
        }
        stage('Build the application') {
            when {
                anyOf {
                    branch 'main'
                }
            }
            steps {
                sh 'dotnet build --no-restore'
            }
        }
        stage('Run the tests') {
            when {
                anyOf {
                    branch 'main'
                }
            }
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}