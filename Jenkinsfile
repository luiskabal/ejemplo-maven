pipeline{
agent any
stages{
	stage('Compile'){
		steps{
		  sh './mvnw.cmd clean compile -e'
		}
		
	}
	 stage('Unit Test'){
		steps{
			sh './mvnw.cmd clean test -e'
		}
		
	}

	 stage('Jar'){
		steps{
			sh './mvnw.cmd clean package -e'
		}
		
	}
stage('Nexus Upload'){
			steps {
				nexusArtifactUploader(
				nexusVersion: 'nexus3',
				protocol: 'http',
				nexusUrl: 'http://fcbfd6a37fff.ngrok.io/',
				groupId: 'com.devopsusach2020',
				version: '0.0.1',
				repository: 'test-nexus',
				credentialsId: 'nexus',
				artifacts: [
					[artifactId: 'DevOpsUsach2020',
					classifier: '',
					file: 'C:/TestJenkins/ejemplo-maven/build/DevOpsUsach2020-0.0.1.jar',
					type: 'jar']
				]
				)
				}
		}
	
}
}

