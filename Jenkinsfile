pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        
        stage('deploy to QA'){
            steps {
                input(message: 'Do you like Java?', ok: 'Yes', 
                        parameters: [booleanParam(defaultValue: true, 
                        description: 'If you like Java, just push the button',name: 'Yes?')])
                echo "deplyoing to QA"
                
            }
        }
        
        stage('QA') {
            steps {
                echo 'Testing..'
                git credentialsId: 'SumitJain0612', url: 'https://github.com/SumitJain0612/TestingCICD.git'
                
               
            }
        }
        
        stage('Deploy to LTE') {
            steps {
                echo 'Deploying....'
            }
        }
        
        stage('LTE') {
            steps {
                echo 'Deploying....'
            }
        }
        
         stage('UAT') {
            steps {
                echo 'Deploying....'
            }
        }
        
        stage('Deply yo prod') {
            steps {
                echo 'Deploying....'
            }
        }
        
        stage('Sanity') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
