pipeline {
    agent any

    parameters {
    string(name: 'Env', defaultValue: 'Test', description: 'Env to deploy')
    booleanParam(name: 'executeTests', defaultValue: true, description: 'Decide whether to run test cases')
    choice(name:'APPVERSION',choices:['1.1','1.2','1.3'])
}
    stages {
        stage ('Compile') {
            steps{
                echo "Compile the Code ${params.APPVERSION}"
            }
        }            
        stage ('UnitTest') {
            when {
    expression {
        params.executeTests == true
    }
}

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