pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/dobrogo-dnia/it-lw4.git', 
                     credentialsId: '442aed03-600c-4e52-9bf6-145cf109363d', 
                     branch: 'main'
            } 
        }
    
        stage('Build') {
            steps {
                bat '"D:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\MSBuild\\Current\\Bin\\MSBuild.exe" test_repos.sln /p:Platform=x64 /p:Configuration=Release /p:WindowsTargetPlatformVersion=10.0.22621.0'
            }    
        }

        stage('Test') {
            steps {
                bat 'x64\\Debug\\test_repos.exe --gtest_output=xml:test_report.xml'
            }
        }
    }
    
    post {
        always {
            junit 'test_report.xml'
        }
    }
}