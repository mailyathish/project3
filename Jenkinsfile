pipeline {
    agent any
	
	  tools
    {
       maven "Maven"
    }
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/mailyathish/project3.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        

  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t rajuyathi/samplewebapp:latest .' 
                //sh 'docker tag samplewebapp rajuyathi/samplewebapp:latest'
                //sh 'sudo docker tag samplewebapp rajuyathi/samplewebapp:$BUILD_NUMBER'
               
          }
        }

	stage('Push Docker Image'){
	steps {
	
	withCredentials([string(credentialsId: 'DockerPWD', variable: 'DockerPass')]) {
    	// some block

	sh 'docker login -u rajuyathi -p ${DockerPass}'

	}
	 // some block
	// sh 'docker push rajuyathi/samplewebapp:latest'

	}

	}
	}
    }    
