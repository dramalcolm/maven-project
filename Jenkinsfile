
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
                build job: 'maven-deploy-to-staging'
            }
        }

        stage('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message: 'Approve PRODUCTION Deployment?'
                }
                build job: 'maven-deploy-to-production'
            }
            post{
                success{
                    echo 'Code deployed to Production.'
                }
                failure{
                    echo 'Deployment failed.'
                }
            }
        }
    }
}