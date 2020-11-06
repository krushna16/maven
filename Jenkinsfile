pipeline
{
    agent any
    stages
    {
        stage('ContinousDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContinousBuild')
        {
            steps
            {
               sh 'mvn package'
            }
        
        }
        stage('ContinousDeployment')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@10.0.1.5:/var/lib/tomcat8/webapps/qaapp.war'
            }
        
        }
        stage('ContinousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
		        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar'
            }
        
        }

	stage('ContinousDelivery')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@10.0.1.6:/var/lib/tomcat8/webapps/prodapp.war'
	        }
        
        }
        
    }
}
