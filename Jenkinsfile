pipeline {
    agent any
    tools {
        maven 'maven' 
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        
        stage('deploy to QA'){
            steps {
                input(message: 'Do you want to push the build to QA?', ok: 'Confirm', 
                        parameters: [booleanParam(defaultValue: true, 
                        description: 'Do you want to push the build to QA?')])
                echo "deplyoing to QA"
                
            }
        }
        
        stage('QA') {
            steps {
                echo 'Testing..'
                git credentialsId: 'SumitJain0612', url: 'https://github.com/SumitJain0612/TestingCICD.git'
                
                sh 'mvn test'
               
            }
        }
        
        
        stage('LTE') {
            steps {
                   echo 'Deployed to LTE'
            }
        }
        
        stage('LT Approval') {
            steps { 
              script {
                    env.RELEASE_SCOPE = input message: 'You want to run the load tests??', ok: 'Confirm!',
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
        
        stage('Deply To prod') {
            steps {
                input(message: 'Do you want to push the build to Production?', ok: 'Confirm', 
                        parameters: [booleanParam(defaultValue: true, 
                        description: 'Do you want to push the build to QA?',name: 'Yes?')])
                echo "deplyoing to Prod"
                
            }
        }
    }
}
