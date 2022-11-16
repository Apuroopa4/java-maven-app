
pipeline{
     	  agent
    		{
    		 label "slave"
		}
    tools{
    	 	maven "m1"
    	}
    stages {
        
        stage('clone') {
            steps{
            git 'https://github.com/Apuroopa4/Amazon123.git'
        }
        }
        stage('build') {
			steps {
			  sh 'mvn -f /var/lib/jenkins/workspace/pipeline_amazon/Amazon/pom.xml -DskipTests clean install'
				
			}
		}
		stage('Test') {
			steps {
			   sh 'mvn -f /var/lib/jenkins/workspace/pipeline_amazon/Amazon/pom.xml test'
			}
			post {
				always {
					junit '**/target/surefire-reports/*.xml'
				}
		
	    	}
		}
        stage('deploy') {
			steps {
			           sh 'cp Amazon/Amazon-Web/target/*.war /var/opt/tomcat/webapps'

			}
        }
	}
    post {
    always
    {
    echo 'finished'
    deleteDir()
}
    }
