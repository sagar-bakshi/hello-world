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
        stage('Deploy Build in staging area'){

            steps{
                build job : 'Deploy-StagingArea-Pipline'
            }
        }

        stage('Deploy build in prodcution'){
            steps{
                timeout (time: 5, unit: 'DAYS'){
                    input message: 'Approgitve Production Deployment'
                }
                build job : ''
            }

            post{
                success{
                    echo 'Deployment on Production successful'
                }

                failure{
                    echo 'Deployement on Production Failure'
                }
            }
        }
    }
}
