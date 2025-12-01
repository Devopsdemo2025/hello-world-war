pipeline {
    agent none
//agent { label 'java' }
    parameters {
        string(name: 'MAVEN_CLEAN', defaultValue: '', description: 'Enter clean command')
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
                  //  steps {
                    /*    withCredentials([
                            usernameColonPassword(
                                credentialsId: 'f6915832-0fba-4dd5-86a9-edb503cb7651',
                                variable: 'userandpass'
                            )
                        ]) { */
                           /* sh """
                                sudo cp /home/slave1/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war \
                                /opt/apache-tomcat-11.0.14/webapps
                            """  */

                            // From job running in slave1 and deploying in master machine tomcat server
                           sh "scp /home/slave1/workspace/HelloWorld_Pipeline/target/hello-world-war-1.0.0.war jenkins@172.31.6.162:/opt/apache-tomcat-11.0.14/webapps"
                        }
                   // }
                //}

            } // parallel
        } // Hello-world
    } // stages
} // pipeline
