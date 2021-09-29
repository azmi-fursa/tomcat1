pipeline
{
	agent {label 'slave'}

	stages{	
		stage('Clone and Build Project'){
			steps{
				git 'https://github.com/jleetutorial/maven-project.git'
				sh "pwd"
				dir ('maven-project'){
				sh "pwd"
		  	        }

				sh 'mvn clean install'
				archiveArtifacts artifacts: '**/*.war', followSymlinks: false
				}	
			}

		stage('Copy Artifacts'){
			steps{
				copyArtifacts filter: '**/*.war', fingerprintArtifacts: true, projectName: 'maven_pipeline', selector: lastSuccessful()
			}
		}
		stage('Deploy Artifacts'){
			steps{
				deploy adapters: [tomcat9(credentialsId: 'e03fd0c0-c335-43b6-bdf5-9f4a2bf70fb6', path: '', url: 'https://172.31.15.52:8888/')], contextPath: null, war: '**/*.war'				
		      	}
			}
	}
}

