pipeline {
    
    agent any
    
    triggers {
        githubPush()
    }

    stages {
        stage('Restore dependencies') {
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                sh 'dotnet restore'
            }
        }

        stage('Build the project') {
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                sh 'dotnet build --no-restore'
            }
        }

        stage('Run the required tests') {
            when {
                expression {
                    return env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                sh 'dotnet test --no-build --no-restore'
            }
        }
    }
}
