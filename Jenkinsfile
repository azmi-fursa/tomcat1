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

script {
"./mvnw package"
      }
		     }
					}

stage('Copy WAR artifacts'){
	steps{
		copyArtifacts filter: '**/*.war', fingerprintArtifacts: true, projectName: 'maven_pipeline', selector: lastSuccessful()
      }
}
}
}
