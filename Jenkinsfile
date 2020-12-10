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
	stage('sonar'){
		steps{

			withSonarQubeEnv('sonar') { 
			  sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
			}
		}
		
	}

	 stage('uploadNexus'){
		freeStyleJob('test-nexus2-tarea') {
			steps {
			  nexusArtifactUploader {
				nexusVersion('nexus3')
				protocol('http')
				nexusUrl('fcbfd6a37fff.ngrok.io')
				groupId('org.springframework.boot')
				version('2.3.4.RELEASE')
				repository('test-repo')
				credentialsId('nexusNgrok')
				artifact {
					artifactId('DevOpsUsach2020')
					type('jar')
					classifier('debug')
					file('C:\TestJenkins\ejemplo-maven\build\DevOpsUsach2020-0.0.1.jar')
				}
				
			  }
			}
		}
		
	}	
}
}

