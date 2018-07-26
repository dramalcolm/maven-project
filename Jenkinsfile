
pipeline{
    agent any
    tools {
        maven 'M3'
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