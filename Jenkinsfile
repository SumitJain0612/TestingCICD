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
                echo "deplyoing to QA"
            }
        }
        
        stage('QA') {
            steps {
                echo 'Testing..'
                git credentialsId: 'SumitJain0612', url: 'https://github.com/SumitJain0612/TestingCICD.git'
                
                sh 'mvn clean package'
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
