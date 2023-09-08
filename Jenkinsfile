node('DOTNETCORE'){
	stage('SCM'){
		checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false,
		extensions: [], submoduleCfg: [], userRemoteConfigs: [[ url: '''https://github.com/msfs-junin/MiAppParaJenkins''']]])
	}
	stage('Build'){
		sh 'dotnet build ConsoleApp1.sln'
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
