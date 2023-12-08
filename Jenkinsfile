pipeline {
    agent any

    environment {
        MSBUILD_PATH = "C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\BuildTools\\MSBuild\\Current\\Bin\\MSBuild.exe"
        PUBLISH_PATH = "D:\\nasb_deployments\\published"
    }

    stages {
        stage('Build') {
            steps {
                bat 'nuget restore'
                bat "\"${MSBUILD_PATH}\" /p:Configuration=Release"
            }
        }

        stage('Copy to Published') {
            steps {
                bat "xcopy /E /Y .\\bin\\Release\\* \"${PUBLISH_PATH}\""
            }
        }
    }

    post {
        success {
            echo "Build succeeded! Add your success actions here."
            // For example, trigger downstream jobs or send notifications
        }
        failure {
            echo "Build failed! Add your failure actions here."
            // For example, send notifications or clean up resources
        }
    }
}
