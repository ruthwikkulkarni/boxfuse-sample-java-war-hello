pipeline{
	agent any
		tools {
			maven '3.8.1'
			}
			stages{
				stage("SCM Checkout"){
					steps{
						checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '9b0873c3-5f40-4b11-b389-46c178acedbd', url: 'https://github.com/ruthwikkulkarni/boxfuse-sample-java-war-hello.git']]])
						}
					}
				stage("Build"){
					steps{
						sh 'mvn --version'
						sh "mvn clean install"
                            }
						}
					stage("Deploy") {
					    steps {
					        deploy adapters: [tomcat9(credentialsId: '1f964824-ea7e-4cb4-8364-1fbdbe136f3e', path: '', url: 'http://localhost:8092/')], contextPath: null, war: '**/*.war'
					}
					}
				}
		}
