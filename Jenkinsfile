pipeline{
	agent any
	tools{
		maven 'maven3.9'
		}
		stages{
			stage("CheckoutCode"){
				steps{
					echo "Checkout started"
					git branch: 'main',url: 'https://github.com/gunubiswal/java-web-app.git'
					echo "checkout completed"
				}
			}
		
			stage("BuildCode"){
				steps{
					echo "Build started"
					sh 'mvn clean package'
					echo "Build completed"
				}
			}
			stage("Deployment"){
				steps{
					echo "deployment started"
					deploy adapters: [tomcat9(credentialsId: 'tomcatcred',url:'http://13.229.129.215:8080/')],contextPath: 'welcomeapp',war: '*/.war'
					echo "Deployemnt completed"
				}
			}

		}
	
}