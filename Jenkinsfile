pipeline {
    agent any
	

 stages {
      stage('checkout') {
           steps {
             
            checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '8956f257-38ec-4c57-ab0f-0c62ae697bd7', url: 'https://github.com/mallsubhrakanta/devopsclass-2.git']]])
             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t devopsclass2 .' 
                sh 'docker tag devopsclass2 mallsubhrakanta/devopsclass2:latest'
                
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
        steps {
          withDockerRegistry(credentialsId: 'docker-token', url: '') {
		  sh  'docker push mallsubhrakanta/devopsclass2:latest'
    
	        }  
          }
        }
       }
	}
