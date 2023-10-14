pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {	
		    sh 'rm -rf hello-world-war'
                    sh 'git clone https://github.com/prasadpvv001/hello-world-war/'
            }
        }
	stage('Build') {
            steps {		
			
                sh 'mvn clean package'
            }
        }

	stage('Push artifacts into artifactory') {
            steps {
              rtUpload (
                serverId: 'my-artifactory',
                spec: '''{
                      "files": [
                        {
                          "pattern": "*.war",
                          "target": "example-repo-local/"
                        }
                    ]
                }'''
              )
	    }
	}
	    
	stage('Deploy') {
            steps {		
			
                sh 'echo Deployed'

            }
        }
	    
    }
}
