pipeline {
    agent any
    stages {
        stage("copy files to ansible server") {
            steps {
                script {
                    echo "copying all necessary files to ansible control node"
                    sshagent(['ansible-server-key']) {
                        sh "scp -o StrictHostKeyChecking=no ansible/* root@206.81.7.158:/root"

                        // this part makes sure Ansible has the necessary private key to execute against EC2
                        withCredentials([sshUserPrivateKey(credentialsId: 'ec2-server-key', keyFileVariable: 'keyfile', usernameVariable: 'user')]) {
                            sh "scp ${keyfile} root@206.81.7.158:/root/ssh-key.pem"
                        }
                    }
                }
            }
        }
    }   
}