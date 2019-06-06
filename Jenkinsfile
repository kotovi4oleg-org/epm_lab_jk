pipeline {
    agent any
    stages {
        stage('SonarQube') {
            steps {
                script {
                   scannerHome = tool 'SonarMSBuild'
                   scannerBuild = "${scannerHome}/SonarScanner.MSBuild.dll"
                   projectKey = env.GIT_COMMIT
                }
                withSonarQubeEnv('SonarServer') {
                    echo %SONAR_HOST_URL%
                    sh "dotnet ${scannerBuild} begin /k:${projectKey} /n:${projectKey} /v:1.0 /d:sonar.host.url=http://127.0.0.1:9000 /d:sonar.issuesReport.html.enable=true"
                    sh 'dotnet build'
                    sh "dotnet ${scannerBuild} end"
                }
            }
        }
    }
}
