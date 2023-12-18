pipeline {
    agent any

    tools {
        maven 'maven3.9'
    }
    stages {
        stage("checkout code") {
            steps {
                script {
                    echo "checkout code started"
                    git branch: 'main', url: 'https://github.com/gunubiswal/java-web-app.git'
                    echo "checkout completed"

                }
            }
        }
        stage("Build code")
             steps{
                echo "Build Code started"
                sh "mvn Clean package"
                echo "Build Code Completed"
             }
        stage("Deployment") {
            steps {
                script {
                    echo "Deployment started"
                    deploy adapters: [tomcat9(url: 'http://13.229.129.215:8080/', credentialsId:'tomcred')], war 
                }
            }
        }    

    }
}