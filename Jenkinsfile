pipeline{
 agent any
  stages{
   stage('Checkout'){
    steps{
	 git url: 'https://github.com/palwalun/secret-santa-application.git',
	 branch: 'master'
	}
    stage('Build'){
    steps{
	 sh 'docker build -t santa-app .'
	 }
    }
  
  }
 } 

}