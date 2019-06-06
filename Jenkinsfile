pipeline {
    agent any
    stages {
        stage('SonarQube') {
            steps {
                script {
                   scannerHome = tool 'SonarMS'
                   scannerBuild = "${scannerHome}\\SonarScanner.MSBuild.dll"
                }
                withSonarQubeEnv('Sonar MS') {
                    bat "dotnet \"${scannerBuild}\" begin /k:%GIT_AUTHOR_NAME% /n:%GIT_AUTHOR_NAME% /v:1.0 /d:sonar.host.url=%SONAR_HOST_URL% /d:sonar.issuesReport.html.enable=true"
                    bat 'dotnet build'
                    bat "dotnet \"${scannerBuild}\" end"
                }
            }
        }
    }
}
