pipeline {
    agent any
    stages{
        stage('poll SCM'){
            steps{
                git credentialsId: 'jnks-pvt', url: 'git@github.com:Naveen-100/docker-play.git'
            }
        }
        stage('docker-ansible'){
            steps{
                ansiblePlaybook credentialsId: 'jnks-pvt', disableHostKeyChecking: true, inventory: 'dev.inv', playbook: 'docker.yml'
            }
        }
        stage('tomcat-ansible'){
            steps{
                ansiblePlaybook credentialsId: 'jnks-pvt', disableHostKeyChecking: true, inventory: 'dev.inv', playbook: 'tomcat.yml'
            }
        }
        stage('deploy-ansible'){
            steps{
                ansiblePlaybook credentialsId: 'jnks-pvt', disableHostKeyChecking: true, inventory: 'dev.inv', playbook: 'deploywar.yml'
            }
        }
        stage('deploy-war-tomcat-ansible'){
            steps{
                ansiblePlaybook credentialsId: 'jnks-pvt', disableHostKeyChecking: true, inventory: 'dev.inv', playbook: 't2.yml'
            }
        }
    }
}