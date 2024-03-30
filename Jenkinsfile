pipeline {
    agent none

    tools{
        //jdk 'myjava'
        maven 'mymaven'
    }

    stages {
        When{
            expression{
                BRANCH_NAME == 'dev'
            }
        }

        stage ('Compile') {
            agent any
            steps{
                echo "Compile the Code"
                sh 'mvn compile'
            }
        }            
        stage ('UnitTest') {
            agent any
            steps{
                echo 'Run the test Code'
                sh 'mvn test'
            }
            post{
                always{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }            
        stage ('Pakage') {
           // agent {label 'linux_slave'}
            agent any
            steps{
                sshagent(['build-server-key']) {
                echo "Run the Paakge Code"
               // sh 'mvn package'
                sh "scp -o StrictHostKeyChecking=no server-script.sh ec2-user@172.31.25.40:/home/ec2-user"
                sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.25.40 ~/server-script.sh"
               // sh "ssh -o ec2-user@172.31.25.40 sudo docker build -t imagename  /home/ec2-user/addressbook"
                
                }       
           }
        }

    }
}
