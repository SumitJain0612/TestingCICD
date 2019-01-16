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
        
        
        stage('LTE') {
            steps {
                   echo 'Deployed to LTE'
            }
        }
        
        stage('Want to run Load Test') {
            steps {
              //  input(message: 'Do you want to push the build to LTE?', ok: 'Yes', 
               //         parameters: [booleanParam(defaultValue: true, 
             //           description: 'Do you want to push the build to QA?',name: 'Yes?')])
              //  echo "deplyoing to LTE"
                //Do you want to push the build to LTE or skip the LTE step and move to UAT?'
                
              script {
                    env.RELEASE_SCOPE = input message: 'You want to run the load tests??', ok: 'Release!',
                            parameters: [choice(name: 'RELEASE_SCOPE',
                                                choices: 'Yes\nNo',
                                                description: 'You want to run the load tests??')]
                }
                echo "${env.RELEASE_SCOPE}"
                
            }
        }
        
        stage('Load Test') {
                when {
                    expression { return env.RELEASE_SCOPE == 'Yes' }
                 }
            steps {
                   echo 'Run load tests'
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
                echo "deplyoing to Prod"
                
            }
        }
    }
}
