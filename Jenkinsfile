pipeline {
    agent any

    stages {
        stage('Validate'){
            steps{
                sh "mvn Validate"
                sh "mvn clean"
            }
        }
        stage('Build'){
            steps{
                sh "mvn compile"
            }    
        }
        stage('Test'){
            steps{
                sh "mvn Test"
            } 
            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'

                }
            }   
        }
        stage('package'){
            steps {

                sh "mvn package"
            }
            post{
                success{
                    archiveArtifacts artifacts: '**/target/**.war', followSymlinks: fals
                }
            }
        }
    }   
}