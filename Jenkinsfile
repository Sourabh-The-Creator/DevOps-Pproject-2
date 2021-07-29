pipeline {
    
    agent any

    tools {
        maven "Maven"
    }

    stages {
         stage("Git pull"){
            steps{
               git 'https://github.com/Sourabh-The-Creator/DevOps-Pproject-2.git'
            }
        } 
        stage("Build Code"){
            steps{
               sh "mvn clean install"
            }
        }  
        stage("Publish to Ansible server"){
            steps{
               sshPublisher(publishers: [sshPublisherDesc(configName: 'ec2 Tomcat Server', transfers: [sshTransfer( execCommand: 'ansible-playbook /etc/ansible/playbooks/deploy.yaml', execTimeout: 120000,   remoteDirectory: '//opt', removePrefix: 'webapp/target', sourceFiles: 'webapp/target/webapp.war')], )])
            }
        }  
        
    }
}