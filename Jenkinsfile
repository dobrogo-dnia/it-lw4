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
                bat 'MSBuild.exe test_repos.sln /p:Platform=x64 /p:Configuration=Release'
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