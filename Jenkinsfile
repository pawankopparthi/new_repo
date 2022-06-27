pipeline{

agent any

tools{
maven 'Maven'
}
environment { 
  GitCred = credentials('GitHub_cred') 
 }
stages{
 stage('Build'){
  steps{
  sh  "mvn clean package"
  }
  }
	
 stage('ExecuteSonarQubeReport'){
  steps{
  sh  "mvn clean sonar:sonar"
  }
  }
  
  stage('UploadArtifactsIntoNexus'){
  steps{
  sh  "mvn clean deploy"
  }
  }
}
}
