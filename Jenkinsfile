pipeline {
    agent 
    {
        label 'built-in'
	    
    }
stages
	{
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
