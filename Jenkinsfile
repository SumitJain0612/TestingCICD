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
            parameters {
            booleanParam defaultValue: true, description: '', name: 'Continue???'
}
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
