pipeline {
    agent none

    tools{
        //jdk 'myjava'
        maven 'mymaven'
    }

    environment {
    IMAGE_NAME = "zaid786/java-mvn-privaterepos:$BUILD_NUMBER"
    BUILD_SERVER_IP = "ec2-user@192.168.2.24"
}


    stages {    
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
                withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {
                echo "Run the Paakge Code"
               // sh 'mvn package'
                sh "scp -o StrictHostKeyChecking=no server-script.sh ${BUILD_SERVER_IP}:/home/ec2-user"
                sh "ssh -o StrictHostKeyChecking=no ${BUILD_SERVER_IP} bash /home/ec2-user/server-script.sh"
                ssh ec2-user@192.168.2.24 sudo docker build -t zaid786/java-mvn-privaterepos:12 /home/ec2-user/addressbook
                #sh "ssh ${BUILD_SERVER_IP} sudo docker build -t ${IMAGE_NAME}  /home/ec2-user/addressbook"
                sh "ssh ${BUILD_SERVER_IP} sudo docker login -u $USERNAME -p $PASSWORD "
                sh "ssh ${BUILD_SERVER_IP} sudo docker push ${IMAGE_NAME}"
                
            }
                
                }       
           }
        }

    }
}
