pipeline{
    agent any
    stages{
        stage("Clone Git Repo"){
            steps{
                git 'https://github.com/RutujaPawal/hello-worldnew.git'
            }
        }
        stage("Build Maven Project"){
            steps{
                sh "mvn clean install"
            }
        }
        stage("Deploy war file on tomcat"){
            steps{
                sshagent(['deployer_user']) {
              sh "scp -v -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@3.111.147.223:/opt/apache-tomcat-8.5.83/webapps"
               }
            }
        }
    }    
}
