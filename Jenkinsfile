
pipeline{
    agent any
    tools {
        maven 'LocalMaven'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/*.war'

                }
            }
        }
        stage('Deploy to Staging'){
            steps{
                build job: 'maven-deploy-to-stage'
            }
        }
    }
}