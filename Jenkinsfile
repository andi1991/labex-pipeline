pipeline {
        agent any
        
        tools {
        maven 'maven3.8.6'
        }

        stages{
            stage('Build'){
                steps {
                    echo "project is building"
                    sh "printenv"
                    sh "mvn clean package"
                }
            }
            stage('Deploy'){
			steps {
				ansiblePlaybook(
					playbook: "${env.WORKSPACE}/playbook.yml",
					inventory: "${env.WORKSPACE}/hosts",
					credentialsId: 'rootID'
				)		
	
			}
		}
        }
}
