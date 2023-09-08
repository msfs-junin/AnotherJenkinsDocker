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
	stage('Package') {
		steps {
			script {
				def buildDir = '.' // Update this path to your actual build directory
				def zipFileName = 'build_result.zip'
				// Create a zip file of the build results
				zip archive: true, dir: buildDir, glob: '**/*', zipFile: zipFileName
			}
		}
	}
	stage('Deploy') {
		steps {
			script {
				def destinationFolder = './destination/folder' // Update this path to your actual destination folder
				def zipFileName = 'build_result.zip'
				// Copy the zip file to the destination folder
				sh "cp ${zipFileName} ${destinationFolder}"
			}
		}
	}
}
