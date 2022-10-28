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
                sshagent(['deploy_user']) {
              sh "scp -v -o StrictHostKeyChecking=no webapp/target/webapp.war ec2-user@43.204.100.249:/opt/tomcat/webapps"
               }
            }
        }
    }    
}
