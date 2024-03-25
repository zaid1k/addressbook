pipeline {
    agent any

    tools{
        jdk 'myjava'
        maven 'mymaven'
    }

    stages {
        stage ('Compile') {
            steps{
                echo "Compile the Code"
                sh 'mvn compile'
            }
        }            
        stage ('UnitTest') {
            steps{
                echo 'Run the test Code'
                sh 'mvn test'
            }
        }            
        stage ('Pakage') {
            steps{
                  echo "Run the Paakge Code"
                  sh 'mvn package'

        }
        }

    }
}
