pipeline{
agent any
stages{
    stage('Compile'){
        steps{
            dir('C:/TestJenkins/ejemplo-maven'){
               sh './mvnw.cmd clean compile -e' 
            }
        }
		
    }
	 stage('Unit Test'){
        steps{
            dir('C:/TestJenkins/ejemplo-maven'){
               sh './mvnw.cmd clean test -e' 
            }
        }
		
    }
	
	 stage('Jar'){
        steps{
            dir('C:/TestJenkins/ejemplo-maven'){
               sh './mvnw.cmd clean package -e' 
            }
        }
		
    }
	stage('sonar'){
		steps{
			withSonarQubeEnv('sonar') { 
			  sh 'mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
			}
		}
		
	}
	
	 stage('Run'){
        steps{
        	dir('C:/TestJenkins/ejemplo-maven') {
				sh 'start mvnw.cmd spring-boot:run'
			}
        }
		
    }
	
	 stage('Test'){
        steps{
            dir('C:/TestJenkins/ejemplo-maven'){
             sh 'start http://localhost:8081/rest/mscovid/test?msg=testing' 
            }
        }
		
    }

}

}

