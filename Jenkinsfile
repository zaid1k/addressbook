pipeline {
    agent none

    tools{
        //jdk 'myjava'
        maven 'mymaven'
    }

    
    stages {
        stage('Check Branch') {
            when {
                expression {
                    BRANCH_NAME == 'dev'
                }
            }
            steps {
                // Steps to execute if the condition is true
            }
        }
        // Define additional stages here
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
