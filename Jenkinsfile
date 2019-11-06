pipeline {
    agent any
    
    stages {
        stage ('No-op') {
            steps {
                sh 'ls'
            }
        }
    }
    
    post{
        always {
            echo 'One way or another, I have finished'
            deleteDir()
        }
        success {
            echo 'I succeeded!'
            mail to: 'lei.fan@capgemini.com',
                subject: 'Succeed Pipline: ${currentBuild.fullDisplayName}',
                body: 'Everything is ok with ${env.BUILD_URL}'
        }
        unstable {
            echo 'I failed'
        }
        failure {
            mail to: 'lei.fan@capgemini.com',
                subject: 'Failed Pipline: ${currentBuild.fullDisplayName}',
                body: 'Something is wrong with ${env.BUILD_URL}'
            
        }
        changed {
            echo 'Things were different before...'
        }
    }
    
}
