pipeline
{
    agent any
    stages
    {
        stage('Continous Download')
        {
            steps
            {
                git 'https://github.com/imrans297/Maven.git'
            }
        }
        stage('Continous Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Continous Deployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclerativePipeline1/webapp/target/webapp.war ubuntu@172.31.55.197:/var/lib/tomcat9/webapps/testing.war'
            }
        }
        stage('Continous Testing')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclerativePipeline1/testing.jar'
            }
        }
        stage('Continous Delivery')
        {
            steps
            {
                input message: 'Need Approval from DM', submitter: 'hari'
                sh 'scp /var/lib/jenkins/workspace/DeclerativePipeline1/webapp/target/webapp.war ubuntu@172.31.56.216:/var/lib/tomcat9/webapps/prodapp.war'
            }
        }
    }
}
