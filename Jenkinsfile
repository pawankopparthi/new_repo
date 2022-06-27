pipeline{

agent any

tools{
maven 'Maven'
}
environment { 
    GitCred = credentials('GitHub_cred') 
 }

stages{
    
  stage('CheckOutCode'){
    steps{
    git branch: 'master', credentialsId: 'GitHub_cred', url: 'https://github.com/pawankopparthi/new_repo.git'
	
	}
  }

 stage('ExecuteSonarQubeReport'){
  steps{
      withSonarQubeEnv(installationName: 'SonarQube', credentialsId: 'token') {
               sh  "mvn clean sonar:sonar"
            }

        }
    }
  
  stage('UploadArtifactsIntoNexus'){
  steps{
  sh  "mvn clean deploy"
  }
  }

}

}
