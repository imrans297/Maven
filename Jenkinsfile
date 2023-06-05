pipeline
{
    agent any
    stages
    {
        stage("Cont_download")
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage("Cont_Build")
        {
            steps
            {
                sh 'mvn package' 
            }
        }
        stage("Con_deployment")
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/Development/webapp/target/webapp.war ubuntu@172.31.31.171:/var/lib/tomcat9/webapps/testapp.war'
            } 
        }
        stage("Cont_Tessting")
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Development/testing.jar'
            }
        }
    }    
    post
    {
        success
        {
            input message: 'Need Approval OFz DM', ok: 'OK', submitter: 'Harish'
            sh 'scp /var/lib/jenkins/workspace/Development/webapp/target/webapp.war ubuntu@172.31.26.241:/var/lib/tomcat9/webapps/prodapp.war'
        }
        failure
        {
            mail bcc: '', body: 'the jenkins CI-CD fails look into it as soon as possible', cc: '', from: '', replyTo: '', subject: 'in Jenkns Prod stage got failure look into it', to: 'imrans-prodteam@ms.com'
        }
    }
}
