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
                def doesJavaRock = input(message: 'Do you like Java?', ok: 'Yes', 
                        parameters: [booleanParam(defaultValue: true, 
                        description: 'If you like Java, just push the button',name: 'Yes?')])

                    echo "Java rocks?:" + doesJavaRock
}
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
