pipeline {
    agent any
    stages {
        stage('InstallMaven') {
            steps {
             sh "sudo update -y"
              sh "sudo apt install maven -y"
            }
        stage('Checkout') {
            steps {
              sh "rm -rf hello-world-war"
              sh "git clone https://github.com/Devopsdemo2025/hello-world-war"
            }
            
        }
    }
}
