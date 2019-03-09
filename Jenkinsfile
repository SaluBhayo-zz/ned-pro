https://github.com/SaluBhayo/ned-pro.git




pipeline {
    agent none
        stages {
        stage('checking out') {
           
            steps { 
             echo "Checking out to Mounted Volume"
              
            }
        }
            stage('Creating Maven Build') {
            
                steps { 
             echo "Building Image in Utility Container"
                    sh 'mvn package'
                    
              
            }
            }
			
            stage('Deploying Package on Tomcat ') {
            
                steps { 
             
                    sh ' '
                    
            }
            }
			   stage('Unpacking Deploy package') {
            agent { label 'wcsv9' }
                steps { 
                            
                   dir ('/home/') {
                   sh 'rm -rf /home/CustDeploy/CusDeploy/*'
                  sh 'unzip wcbd-deploy-server-local-"$apptype"-"$label".zip -d /home/CustDeploy/CusDeploy/'
             
              }
                    
            }
            }
		 stage('Updating Image with Changes ') {
            agent { label 'wcsv9' }
                steps { 
                    dir ('/home/CustDeploy') {
                    sh "docker build -f Dockerfile . -t  commerce/crs-app:9.0.0.1"
                    
                    }
            }
            }	        
		
		stage('Starting Container ') {
            agent { label 'wcsv9' }
                steps { 
                    dir ('/home/') {
                    sh "docker-compose -f docker-compose-auth-crs.xml up -d"
                    
                    }
            }
            }
            
            
            
        }
}
