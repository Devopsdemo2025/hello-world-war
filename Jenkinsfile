
pipeline {
   agent none
  //agent { label 'java' }
  parameters {
        string(name: 'maven clean', defaultValue: '', description: 'Enter clean here')
       // booleanParam(name: 'DEBUG', defaultValue: false, description: 'Enable debug mode')
        choice(name: 'maven build', choices: ['package', 'compile', 'install'], description: 'build project')
    }
   withCredentials([usernamePassword(credentialsId: 'a67f270b-a726-4fe8-9911-35ca43fdee7d', 
                                                 usernameVariable: 'USER', 
                                                 passwordVariable: 'PASS')])

    stages {
        stage('Hello-world') {
          parallel {
            stage('Checkout') {
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
      sh "sudo cp /home/slave1/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war  /opt/apache-tomcat-11.0.14/webapps" 
   //   sh "sudo scp /home/slave1/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war  jenkins@13.204.75.35:/opt/apache-tomcat-11.0.14/webapps/" 
   //   echo "build deployed"

    }
}
          }
        }
    }
}
