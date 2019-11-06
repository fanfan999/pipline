pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    tools {
        maven 'apache-maven-3.0.1'
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
            }
            steps {
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
