pipeline {
    agent any
    triggers { 
        pollSCM('* * * * *') 
    }
    stages {
        stage('SCA') {
            steps {
                checkout scm
                bat 'gradle UiSCA'
            }
        }        
        stage('Dependency Management') {
            steps {
                
                bat 'gradle UiDependencyMgmt'
            }
        }
        stage('Compile & Configure') {
            steps {
                bat 'gradle UiProdBuild'
            }
        }        

        stage('Unit Test') {
            steps {
                bat 'gradle UiUnitTest'
            }
        }
        stage('Publish') {
            steps {
                script {
                    bat "gradle UiPublishReport"
                }
            }
        }
    }
}