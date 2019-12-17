pipeline {
	agent any
	
	options {
		skipStagesAfterUnstable()
		
		timeout(time:1, unit:'HOURS')
	}
	
	environment {
		def USERMAIL = "1058180192@qq.com lei.fan@capgemini.com"
		MAVEN_OPTS="-Xmx125m"
	}

    parameters {
         choice(name: 'CHOICE', choices: ['true', 'false'], defaultValue: true, description: 'Pick something')
    }
	
	stages {
		
		stage('Info') {
			steps {
                echo BRANCH_NAME
				sh 'printenv'
			}
		}
		
		stage('Deploy for development') {
			when {
				expression {
                    BRANCH_NAME == ~ /(dev)/
                }
			}
			
			steps {
				echo 'This deploy process is for development'
			}
			
		}
		
		stage('Deploy for production') {
			when {
				branch 'master'
			}
			 
			steps {
				echo 'This process is for production'
                script {
                    echo 'sh BRAND_NAME == ~/(master)/'           
                }
			}
		}
	}
	
	post {
		always {
			echo "The section will always be shown"
            //删除当前目录
			deleteDir()
		}
		
		success {
            echo 'success sending email'
			script{
				configFileProvider([configFile(fileId: 'caas-email-template-20191216',
											   targetLocation: 'email.html', 
											   variable: 'failt_email_template')]) {
					template = readFile encoding: 'UTF-8', file: "${failt_email_template}"
					emailext(subject: '任务执行成功',
							 attachLog: true,
							 recipientProviders: [requestor()], 
							 to: "${USERMAIL}",
							 body: """${template}""")
					}
				}

		}
		
		failure {
			script{
				configFileProvider([configFile(fileId: 'caas-email-template-20191216',
											   targetLocation: 'email.html', 
											   variable: 'failt_email_template')]) {
					template = readFile encoding: 'UTF-8', file: "${failt_email_template}"
					emailext(subject: '任务执行失败',
							 attachLog: true,
							 recipientProviders: [requestor()], 
							 to: "${USERMAIL}",
							 body: """${template}""")
					}
				}

		}
		
	}
}
