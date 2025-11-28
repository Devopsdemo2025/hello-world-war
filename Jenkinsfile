pipeline {
   // agent none
     agent { label 'java1' }

    stages {
        stage('Checkout') {
    //        agent { label 'java' }
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/Devopsdemo2025/hello-world-war'
            }
        }

        stage('Build') {
      //      agent { label 'java' }
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Whoami') {
  //  agent { label 'java' }
    steps {
        sh 'whoami'
    }
}
        
   stage('Deploy') {
 //   agent { label 'java' }
    steps {
        sh "sudo cp /home/slave2/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war home/apache-tomcat-11.0.14/webapps"
    }
}
    }
}
