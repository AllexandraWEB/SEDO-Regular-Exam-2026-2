pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Restore dependencies') {
            steps {
                sh 'dotnet restore Homies.sln'
            }
        }

        stage('Build the application') {
            steps {
                sh 'dotnet build Homies.sln --no-restore'
            }
        }

        stage('Run the tests') {
            steps {
                sh 'dotnet test Homies.sln --no-build --verbosity normal'
            }
        }
    }
}