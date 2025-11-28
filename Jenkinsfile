pipeline {
   agent none
   //  agent { label 'java' }

    stages {
        stage('Checkout') {
          parallel {
           agent { label 'java' }
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/Devopsdemo2025/hello-world-war'
            }
        }

        stage('Build') {
            agent { label 'java' }
            steps {
                sh 'mvn clean package'
            }
        }
        
   stage('Deploy') {
    agent { label 'java' }
    steps {
        //sh 'sudo cp /home/slave1/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war /home/apache-tomcat-11.0.14/webapps'
       echo "deployed"
    }
}
        }
    }
}
