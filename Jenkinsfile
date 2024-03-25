pipeline {
    agent any

    parameters{
        string(name:'Env',defaultValue: 'Test',description:'Env to deploy')
    }

    stages {
        stage ('Compile') {
            steps{
                echo 'Compile the Code'
            }
        }            
        stage ('UnitTest') {
            steps{
                echo 'Run the test Code'
            }
        }            
        stage ('Pakage') {
            steps{
                echo 'Run the Paakge Code'
            }
        }            
    }
}