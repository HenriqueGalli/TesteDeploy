pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')
    }

    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deployments'){
            parallel {
                stage ('Deploy to Staging'){
                    steps {
                        sh  'git add. | git commit -m "Teste deploy" | git push'
                        
                    }
                }
            }
        }        
    }
}