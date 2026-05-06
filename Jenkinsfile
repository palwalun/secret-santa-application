pipeline{
 agent any
 environment{
  ACR_LOGIN_SERVER = 'devopsproject1.azurecr.io'
  IMAGE_NAME = 'santa-app'
  TAG = 'latest'
  }
  stages{
   stage('Checkout'){
    steps{
	 git url: 'https://github.com/palwalun/secret-santa-application.git',
	 branch: 'master'
	}
   }
    stage('Build'){
    steps{
	 sh 'docker build -t santa-app .'
	 }
    }
   stage('Login to ACR') {
       steps {
         withCredentials([usernamePassword(
             credentialsId: 'acr-creds',
             usernameVariable: 'ACR_USER',
             passwordVariable: 'ACR_PASS'
         )]) {
             sh '''
               echo $ACR_PASS | docker login $ACR_LOGIN_SERVER \
               -u $ACR_USER --password-stdin
             '''
           }
          }
         }
  
 } 

}