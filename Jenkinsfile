pipeline {
    agent none

    parameters {
        string(name: 'MAVEN_CLEAN', defaultValue: 'clean', description: 'Enter clean command')
        choice(name: 'MAVEN_BUILD', choices: ['package', 'compile', 'install'], description: 'Build project')
    }

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
                        sh "mvn ${MAVEN_CLEAN} ${MAVEN_BUILD}"
                    }
                }

                stage('Deploy') {
                    agent { label 'java' }
                    steps {
        withCredentials([usernameColonPassword(credentialsId: 'f6915832-0fba-4dd5-86a9-edb503cb7651', variable: 'userandpass')]) {
    // some block
}
                    }
                            sh """
                                sudo cp /home/slave1/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war \
                                /opt/apache-tomcat-11.0.14/webapps
                            """
                            // sh "scp /path/to/war jenkins:${userandpass}@13.204.75.35:/opt/apache-tomcat-11.0.14/webapps/"
                        }
                    }
                }

            } // parallel end
        } // Hello-world stage end

    } // stages end
} // pipeline end
