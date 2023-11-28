/* groovylint-disable-next-line CompileStatic */
def gv

pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('docker-app') //this can be used accross all stages
    }
    stages {
        stage('init') {
            steps {
                script {
                    gv = load 'script.groovy'
                }
            }
        }
        stage('build') {
            steps {
                echo 'building the application..'
                echo "build version ${NEW_VERSION}"
                nodejs('Node-18.7.0') {
                    sh 'npm install'
                }
            }
        }
        stage('test') {
            // when {
            //     expression {
            //         BRANCH_NAME == 'dev' || BRANCH_NAME == 'main'
            //     }
            // }
            steps {
                script {
                    gv.testApp()
                }
            }
        }
        stage('deploy') {
            steps {
                echo 'deploying the application..'
                echo "some script ${SERVER_CREDENTIALS}"
                // withCredentials([
                //     usernamePassword(credentials: 'docker-app', usernameVariable: USER, passwordVariable: PWD)
                //  ]) {
                //     echo "some script ${USER} ${PWD}"
                //  }
            }
        }
    }
    // post {
    //     always {
    //     }
    //     success {
    //     }
    //     failure {
    //     }
    // }
}
