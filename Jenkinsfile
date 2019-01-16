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
                input(message: 'Do you want to push the build to QA?', ok: 'Yes', 
                        parameters: [booleanParam(defaultValue: true, 
                        description: 'Do you want to push the build to QA?',name: 'Yes?')])
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
              //  input(message: 'Do you want to push the build to LTE?', ok: 'Yes', 
               //         parameters: [booleanParam(defaultValue: true, 
             //           description: 'Do you want to push the build to QA?',name: 'Yes?')])
              //  echo "deplyoing to LTE"
                //Do you want to push the build to LTE or skip the LTE step and move to UAT?'
                
              script {
                    env.RELEASE_SCOPE = input message: 'User input required', ok: 'Release!',
                            parameters: [choice(name: 'RELEASE_SCOPE', choices: 'patch\nminor\nmajor', description: 'Do you want to push the build to LTE or skip the LTE step and move to UAT?')]
                }
                echo "${env.RELEASE_SCOPE}"
                
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
                input(message: 'Do you want to push the build to Production?', ok: 'Yes', 
                        parameters: [booleanParam(defaultValue: true, 
                        description: 'Do you want to push the build to QA?',name: 'Yes?')])
                echo "deplyoing to QA"
                
            }
        }
        
        stage('Sanity') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
