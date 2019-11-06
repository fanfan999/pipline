pipeline {
    agent any
    
    stages {
        stage ('No-op') {
            steps {
                sh 'ls'
            }
        }
        
        stage () {
            steps {
                input 'please input something'
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
            mail to: '1058180192@qq.com',
                subject: 'Succeed Pipline: ${currentBuild.fullDisplayName}',
                body: 'Everything is ok with ${env.BUILD_URL}'
        }
        unstable {
            echo 'Tests failed'
        }
        failure {
            echo 'Process failed'   
        }
        changed {
            echo 'Things were different before...'
        }
    }
    
}
