pipeline{
    agent any
    stages{
        stage('Build Servlet'){
            steps{
                sh 'mvn clean package'
            }
            steps{
                sh 'docker build . -t tomcatwebapp:{$env.BUILD_ID}'
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
