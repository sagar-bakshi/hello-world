pipeline{
    agent any
    stages{
        stage('Build Servlet'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo 'Now Archiving the project to war file'

                    archiveArtifacts artifacts : '**/*.war'
                }
            }
        }
    }
}