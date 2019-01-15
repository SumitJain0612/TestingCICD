pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                git credentialsId: 'SumitJain0612', url: 'https://github.com/SumitJain0612/TestingCICD.git'
                
                sh 'mvn clean package'
            }
        }
        
        stage('deploy to prod'){
            steps {
                if (userInput == true) {
                    // do something
                    echo "this was successful"
                } else {
                    // do something else
                    echo "this was not successful"
                    currentBuild.result = 'FAILURE'
                } 
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    
    def userInput
    try {
        userInput = input(
            id: 'Proceed1', message: 'Was this successful?', parameters: [
            [$class: 'BooleanParameterDefinition', defaultValue: true, description: '', name: 'Please confirm you agree with this']
            ])
    } catch(err) { // input false
        def user = err.getCauses()[0].getUser()
        userInput = false
        echo "Aborted by: [${user}]"
    }
}
