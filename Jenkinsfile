pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'    
    }
   stages{
    stage('Sonar Analysis ') {
             steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=buggweppapp -Dsonar.organization=buggweppapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=224826eb1838f43a892d112bdcc81e54a0c3138f'
			}
    }

	stage('Snyk SCA Analysis') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
