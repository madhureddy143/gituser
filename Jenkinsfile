import groovy.json.JsonSlurper

pipeline{
	agent any
	stages{
		stage('checkout'){
			steps{
				checkout scm
				checkout([$class: 'GitSCM', 
						  branches: [[name: '*/main']],
						  extensions: [], 
						  userRemoteConfigs: [[url: 'https://github.com/madhureddy143/M-benz_assessment2.git']]]
				)
			}
		}
		stage('reportgen'){
			steps{
				bat "echo here report will be generated"
				script{
				  bat "echo i am from the script block"
				   def url ="https://reqres.in/api/users?page=1"
				   def response = bat(script: "curl -s $url, returnStdout: true")
				   echo response
				}
			}
		}
		stage('testing stage'){
			parallel{
				stage('unit test'){
					steps{
						bat "echo unit test stage"
					}
				}
				stage('smoke test'){
					steps{
						bat "echo smoke test stage"
					}
				}
				stage('integration test'){
					steps{
						bat "echo unit test stage"
					}
				}
			}
		}
	}
}
					
