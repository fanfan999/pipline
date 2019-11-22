pipeline {
    agent {
        docker {
            image 'maven:3-jdk-8-openj9'
        }
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
            }
        }
    }
}
