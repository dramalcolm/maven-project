
pipeline{
    agent any

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