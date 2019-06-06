pipeline {
    agent any
    stages {
        stage('SonarQube') {
            steps {
                script {
                   scannerHome = tool 'SonarMS'
                   scannerBuild = "${scannerHome}\\SonarScanner.MSBuild.dll"
                   projectKey = env.GIT_COMMIT
                }
                withSonarQubeEnv('Sonar MS') {
                    bat "dotnet \"${scannerBuild}\" begin /k:${projectKey} /n:${projectKey} /v:1.0 /d:sonar.host.url=%SONAR_HOST_URL% /d:sonar.issuesReport.html.enable=true"
                    bat 'dotnet build'
                    bat "dotnet \"${scannerBuild}\" end"
                }
            }
        }
    }
}
