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
	
	 stage('Run'){
        steps{
      sh 'start mvnw.cmd spring-boot:run'
        }
		
    }
	
	 stage('Test'){
        steps{
          sh 'start http://localhost:8081/rest/mscovid/test?msg=testing' 
        }
		
    }

}

}

