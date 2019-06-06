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
                    bat "dotnet \"${scannerBuild}\" begin /k:MyAppKey /n:MyAppName /v:1.0 /d:sonar.host.url=%SONAR_HOST_URL%"
                    bat 'dotnet build'
                    bat "dotnet \"${scannerBuild}\" end"
                }
            }
        }
    }
}
