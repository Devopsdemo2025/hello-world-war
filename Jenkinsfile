pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
              sh "rm -rf hello-world-war"
              sh "git clone https://github.com/Devopsdemo2025/hello-world-war"
            }
        }
        stage('Build') {
            steps {
              sh "mvn clean package"
            }      
        }
        stage('Deploy') {
            steps {
              sh "cp /var/lib/jenkins/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war /opt/apache-tomcat-11.0.14/webapps/"
            }      
        }
    }
}
