pipeline {  
	agent any
	stages {
		stage ('Test Bed Set Up') { 
			steps {
				dir('C:\\DOCKER\\MSGFW2.0'){
					bat label: '', script: 'docker build --pull --target testrunner -t msgfw2.0:test .'
				}
			}
			post {
                always {
                    echo "Test Bed Set Up currentResult: ${currentBuild.currentResult}"
                }
                failure {
                     input('Build is failed Can we proceed?')
                }
            }
		} 
		stage ('MSGFW2.0 Unit Test Execution') { 
			steps {
				dir('C:\\Docker\\MSGFW2.0'){
					bat label: '', script: 'docker run --rm -v "C:\\Docker\\MSGFW2.0\\Test Results":C:\\app\\msg.Testframework_cs\\TestResults msgfw2.0:test'
				}
			}
			post {
                always {
                    echo "Test Bed Set Up currentResult: ${currentBuild.currentResult}"
                }
                failure {
                     input('Build is failed Can we proceed?')
                }
            }
		}
	}
	post {
        always {
            echo "Pipeline result: ${currentBuild.result}"
         } 
    }
}
