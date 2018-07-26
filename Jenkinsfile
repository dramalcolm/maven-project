
pipeline{
    agent any
    tools {
        maven 'LocalMaven'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean packages'
            }
            post{
                success{
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/*.war'

                }
            }
        }
    }
}