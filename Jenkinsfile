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
archiveArtifacts artifacts: '**/*.war', followSymlinks: false
		     }
					}

}
}
