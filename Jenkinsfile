pipeline
{
    agent any
    stages
    {
        stage('Cont_Download')
        {
            steps
            {
                git 'https://github.com/imrans297/Maven.git'
            }
        }
        stage('Cont_Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Cont_Deployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclerativePipeline1/webapp/target/webapp.war ubuntu@172.31.12.103:/var/lib/tomcat9/webapps/testapp.war'
            }
        }
        stage(COnt_Testing)
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclerativePipeline1/testing.jar'
            }
        }
        stage(Cont_Delivery)
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/DeclerativePipeline1/webapp/target/webapp.war ubuntu@172.31.6.120:/var/lib/tomcat9/webapps/prodapp.war'
            }
        }
    }
}
