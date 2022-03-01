pipeline {
    agent any
    stages {
        stage('Init') {
            steps {
                echo 'Start the pipeline job by Mehdi Jebali'
            }
        }
        stage('Build Application') {
            steps {
                echo 'Build the application'
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Deploy in Staging Environment'){
            steps{
                build job: 'Deploy_App_Staging_Env'
            }   
        }
    }
}