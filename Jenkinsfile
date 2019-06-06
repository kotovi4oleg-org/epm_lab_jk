pipeline {
    agent any
    stages {
        stage('SonarQube') {
            steps {
                script {
                   scannerHome = tool 'SonarMS'
                   scannerBuild = "${scannerHome}\\SonarQube.Scanner.MSBuild.exe"
                }
                withSonarQubeEnv('Sonar MS') {
                    bat "${scannerBuild} begin /k:MyAppKey /n:MyAppName /v:1.0 /d:sonar.host.url=%SONAR_HOST_URL% /d:sonar.login=%SONAR_AUTH_TOKEN%"
                    bat 'dotnet build'
                    bat "${scannerBuild} end /d:sonar.login=%SONAR_AUTH_TOKEN%"
                }
            }
        }
    }
}
