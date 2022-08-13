pipeline{
    agent any
    stages{
        stage('Git clone'){
            steps{
                git credentialsId: 'b9c900d5-80eb-4876-869e-daf320fdb1b6', url: 'https://github.com/Vinho0oNguyen/TTTN.git'
            }
            
        }
        
        stage('Build images'){
            steps{
                sh '''#!/bin/bash
                    ssh ansible@10.104.0.5 -i /home/private_key << EOF
                    cd /etc/ansible/
                    ansible-playbook-2.7 build_image_docker.yml'''
            }
        }
        
         stage('Deploy to k8s'){
            steps{
                sh '''#!/bin/bash
                    ssh ansible@10.104.0.5 -i /home/private_key << EOF
                    cd /etc/ansible/
                    ansible-playbook deploy_k8s.yml'''
            }
        }
        
    }
}
