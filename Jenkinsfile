pipeline {
    agent any

    parameters{
        string(name:'Env',defaultValue: 'Test',description:'Env to deploy')
        booleanParam(name:'executeTests',defaultValue:True,description:'decide to run test case')
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
                echo "Run the Paakge Code in env:${params.Env}"
            }
        }            
    }
}