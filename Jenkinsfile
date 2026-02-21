pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Restore dependencies') {
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build the application') {
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Run the tests') {
            steps {
                sh 'dotnet test --no-build --verbosity normal'
            }
        }
    }
}