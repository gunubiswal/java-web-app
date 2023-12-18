pipeline {
    agent any

    tools {
        maven 'maven3.9'
    }

    stages {
        stage("Checkout Code") {
            steps {
                script {
                    echo "Checking out code..."
                    git branch: 'main', url: 'https://github.com/gunubiswal/java-web-app.git'
                    echo "Checkout completed."
                }
            }
        }

        stage("Build Code") {
            steps {
                echo "Building Code..."
                sh "mvn clean package"
                echo "Build completed."
            }
        }

        stage("Deployment") {
            steps {
                script {
                    echo "Deploying to Tomcat..."
                    deploy adapters: [tomcat9(url: 'http://13.229.129.215:8080/', credentialsId: 'tomcatcred')],
                           contextPath: "welcomeapp", war: "**/*.war"
                    echo "Deployment completed."
                }
            }
        }
    }

}
