pipeline {
    agent {
        node {
            label 'DOTNETCORE'
        }
    }
    
    stages {
        stage('SCM') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false,
                extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/msfs-junin/MiAppParaJenkins']]])
            }
        }
        
        stage('Build') {
            steps {
                sh 'dotnet build ConsoleApp1.sln'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Execute unit tests'
            }
        }
        
        stage('Package') {
            steps {
                script {
                    def buildDir = 'path/to/your/build/directory' // Update this path to your actual build directory
                    def zipFileName = 'build_result.zip'
                    
                    // Create a zip file of the build results
                    zip archive: true, dir: buildDir, glob: '**/*', zipFile: zipFileName
                }
            }
        }
        
        stage('Deploy') {
             steps {
                echo 'Deploying'
            }
        }
    }
}
