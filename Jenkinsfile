pipeline {
	agent any

	stages {
		stage('Checkout') {
			steps {
				git url: 'https://github.com/dobrogo-dnia/it-lw4.git', credentialsId: '442aed03-600c-4e52-9bf6-145cf109363d'
			} 
		}
	
		stage('Build') {
			steps {
				// Крок для збірки проекту з Visual Studio
				// Правильні шляхи до рішення/проекту та параметри MSBuild
				bat 'MSBuild.exe test_repos.sln /p:Platform=x64 /p:Configuration=Release
			}	
		}

		stage('Test') {
			steps {
			// Команди для запуску тестів
			bat "x64\\Debug\\test_repos.exe --gtest_output=xml:test_report.xml" }
		}
	}
	
	post {
	always {
		// Publish test results using the junit step
		// Specify the path to the XML test result files 
		junit 'test_report.xml'
	}
}
}