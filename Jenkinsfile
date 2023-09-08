node('DOTNETCORE'){
	stage('SCM'){
		checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false,
		extensions: [], submoduleCfg: [], userRemoteConfigs: [[ url: '''https://github.com/FeynmanFan/JenkinsDocker''']]])
	}
	stage('Build'){
		sh 'dotnet build ConsoleApp1'
	}
	stage('Test'){
		echo 'Execute unit tests'
	}
	stage('Package'){
		echo 'zip it up'
	}
	stage('Deploy'){
		echo 'Push to deployment'
	}
}
