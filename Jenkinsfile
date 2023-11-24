pipeline{
    agent any
    stages{
        stage('build'){
            steps{
                echo 'building the application..'
                nodejs('Node-18.7.0'){
                    sh 'npm install'
                }
            }
        }
        stage('test'){
             steps{
                echo 'Testing the application..'
            }
        }
    }
}