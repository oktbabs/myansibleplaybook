pipeline {
    agent any

    stages {
        stage('SCM chekcout') {
            steps {
                echo 'Checking out form GIT'
                git credentialsId: '73b3562f-8684-4049-a7c1-ff8983c89640', url: 'https://github.com/oktbabs/myansibleplaybook.git'
            }
        }
        stage('ssh to OTD Server') {
            steps {
            sshagent(['ansible2']) {
              sh 'ssh -o StrictHostKeyChecking=no  oracle@192.168.10.107' 
                              ansiblePlaybook credentialsId: 'ansible', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'hosts', playbook: 'jenkins-playbook.yaml'
                }
            }
        }
        stage('Execute Playbook') {
            steps {
                echo "Today is good"
//              ansiblePlaybook credentialsId: 'ansible', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'hosts', playbook: 'jenkins-playbook.yaml'
            }
        }

    }
}
