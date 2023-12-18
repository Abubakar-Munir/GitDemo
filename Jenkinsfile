pipeline {
    agent any

    environment {
        MSBUILD_PATH = "C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\MSBuild\\Current\\Bin\\MSBuild.exe"
        PUBLISH_PATH = "d-ntools\\itapps\\Jenkins-CI-CD"
    }

    stages {
        stage('Build') {
            steps {
                bat "\"${MSBUILD_PATH}\" WindowsFormsApp1.sln /p:Configuration=Release"
            }
        }

        stage('Publish') {
            steps {
                bat "xcopy /E /Y .\\bin\\Release\\* \"${PUBLISH_PATH}\""
            }
        }
    }

    post {
        success {
            echo "Build and publish succeeded! Add your success actions here."
        }
        failure {
            echo "Build or publish failed! Add your failure actions here."
        }
    }
}
