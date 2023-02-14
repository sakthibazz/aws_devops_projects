pipeline 
{
    agent any




    stages
    {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM'])
            }
        }
        stage("Git Clone") 
        {
            
            steps {
                git 'https://github.com/sakthibazz1/javaproject.git'
                  }
         }
            stage("Maven Builds")
            {
            steps {              
                sh "mvn validate"
                sh "mvn clean"
                sh "mvn compile"
                sh "mvn install"
                sh "mv target/*.war target/chumma.war"
                  }
            }
            stage("deploy")
            {
                steps{
                sshagent(['sakthi']) 
                    {   
                    sh """
                    scp -o StrictHostKeyChecking=no target/chumma.war ec2-user@172.31.48.113:/usr/local/apache-tomcat-8.5.85/webapps/
                    ssh ec2-user@172.31.48.113 /usr/local/apache-tomcat-8.5.85/bin/shutdown.sh
                    ssh ec2-user@172.31.48.113 /usr/local/apache-tomcat-8.5.85/bin/startup.sh
                    """
                
                    }
                }
            }
    }
}