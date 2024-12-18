pipeline {
    agent 
    {
        label 'built-in'
	    customWorkspace '/mnt/multi-b/'
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
                git credentialsId: 'git-1', url: 'https://github.com/leenadharmik/project.git'
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
    stage('Deploy-WAR-on-slave3')
    {
	
    steps
    {
        echo "Deploying WAR to Slave3 machine"
        sh 'sudo scp /target/LoginWebApp.war leena@172.31.38.237/mnt/servers/apache-tomcat-9.0.98/webapps'
    }
    }
    
    }
}
