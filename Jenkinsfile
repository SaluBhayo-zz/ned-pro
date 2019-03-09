https://github.com/SaluBhayo/ned-pro.git




pipeline {
    agent any
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
}
