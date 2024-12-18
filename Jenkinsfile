pipeline {
	//updateforWebhook
    agent 
    {
        label 'built-in'
	    
    }
tools 
{
    maven 'My-Maven'
}
    stages 
    {
        stage('git-pull') 
        {
            steps {
                echo 'Pulling Code from GIT'
                git branch: 'dev', credentialsId: 'git-1', url: 'https://github.com/leenadharmik/jenkins_pro.git'
            }
        }
    stage('build-rar-master')
    {
        steps
        {
        echo "Building rar file on Jenkins-Master"
        sh 'mvn clean install'
        }
    }
    stage('Deploy-WAR-on-slave2')
    {
	
    steps
    {
        echo "Deploying WAR to Slave2 machine"
        sh 'sudo scp -r /root/.jenkins/workspace/Assign-Multi-branch_master/target/LoginWebApp.war leena@172.31.46.11:/mnt/servers/apache-tomcat-9.0.98/webapps'
    }
    }
    stage('start-tomcat')
	{
		agent
		{
			label 'slave2'
		}
		steps
		{
			echo "Starting tomcat"
			sh 'cd /mnt/servers/apache-tomcat-9.0.98/bin && sudo ./startup.sh'
		}
		
	}
	
}
}
