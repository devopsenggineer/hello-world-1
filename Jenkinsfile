pipeline {
    agent any
   // environment {
   //     PATH = "/opt/apache-maven-3.6.3/bin:$PATH"
   // }
    stages {
//        stage("clone code"){
//            steps{
//               git credentialsId: 'git_credentials', url: 'https://github.com/devopsenggineer/hello-world-1.git'
//            }
//        }
        stage("build code"){
             tools {
                   maven "Maven3"
                }

            steps{
              sh "mvn clean install"
            }
        }
        stage("deploy"){
            steps{
              sshagent(['tomcat-server-private-key-ID']) {
                 sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war osboxes@192.168.0.3:/home/osboxes/apache-tomcat-8.5.65/webapps"
                 
                }
            }
        }
    }
}
