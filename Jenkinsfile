pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    tools {
        maven 'Maven3.6.2'
    }
    
    stages {
        stage ('Build') {
            steps {
                echo 'Building'
            }
        }
        
        stage ('Test') {
            steps {
              echo 'Testing'
                sh 'mvn --version'
            }
        }
        
        stage ('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}
