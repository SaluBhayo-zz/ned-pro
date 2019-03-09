https://github.com/SaluBhayo/ned-pro.git




pipeline {
    agent any
        stages {
        stage('checking out') {
           
            steps { 
             echo "Checking Out Code!"
              
            }
        }
            stage('Creating Maven Build') {
            
                steps { 
             echo "Building Image in Utility Container"
                    sh 'cd /var/lib/jenkins/workspace/CI-CD-NED-Project/jsp-helloworld && mvn package'
                    
              
            }
	    }
	
		stage('Deploying War to Tomcat ') {
            
                steps { 
             echo "Deploying in Tomcat"
                    sh 'cp /var/lib/jenkins/workspace/CI-CD-NED-Project/jsp-helloworld/target/jsp-helloworld-1.0-SNAPSHOT.war /opt/tomcat/apache-tomcat-9.0.16/webapps/ned.war '
                    
           
			
		}
		}
		
	
		 stage('Stopping Tomcat') {
            
                steps { 
             echo "Building Image in Utility Container"
                    sh 'sh /opt/tomcat/apache-tomcat-9.0.16/bin/shutdown.sh'
                    
              
            }
	    }
	        
		
		
		stage('Starting Tomcat ') 
{
    build 'Tomcat-Start'
}
            
                
	        
            
            
            
        }
}
