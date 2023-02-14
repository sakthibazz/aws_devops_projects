pipeline 
{
    agent any




    stages
    {
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
                sh "mvn package"
                  }
            }
    }
}