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
        // stage('Public test') {
        //     steps {
                
        //         junit '**/target/surefire-reports/TEST-*.xml'
        //         jacoco()
        //     }
        // }
        
        stage('Deploy') {
            steps {
                
                sh 'echo "Hello"'
                sh 'ls'
                sh 'pwd'
                sh 'cp webapp/target/webapp.war .'
                sh 'rm -rf Dockerfile README.md appspec.yml pom.xml server/ webapp Jenkinsfile'
                sh "zip webapp.zip webapp.war"
                sh "aws deploy push --application-name cicd-codedeploy --s3-location s3://cicd-project-adyraj/webapp.zip --ignore-hidden-files --region ap-south-1"
            }
        }
    }
}

