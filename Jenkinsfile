pipeline {
    agent any

    stages {
        stage('Clone Code')
        {
            steps{
                // Get some code from a GitHub repository
                git 'https://github.com/adityarajttn/hello-world.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'sudo cp webapp/target/webapp.war .'
                sh 'sudo rm -rf Dockerfile README.md pom.xml server/ webapp Jenkinsfile'
                sh "sudo zip webapp.zip webapp.war"
                sh "aws deploy push --application-name cicd-codedeploy --s3-location s3://cicd-project-adyraj/webapp.zip --ignore-hidden-files --region ap-south-1"
            }
        }
    }
}

