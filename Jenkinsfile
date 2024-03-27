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
            agent {label 'linux_slave'}
            steps{
                  echo "Run the Paakge Code"
                  sh 'mvn package'

        }
        }

    }
}
