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
            //step([$class: 'XrayImportBuilder', endpointName: '/xunit', importFilePath: 'FrameworkReport.XML', importToSameExecution: 'true', projectKey: 'COV', serverInstance: 'CLOUD-7f86a19a-07b8-4fdb-96c8-abb3bbead4c0'])
		//step([$class: 'XrayImportBuilder', endpointName: '/xunit', importFilePath: 'Resultfile.xml', importToSameExecution: 'true', projectKey: 'COV', serverInstance: 'CLOUD-3f0b34ae-2880-4013-9571-41ed5f13027f'])
        step([$class: 'XrayImportBuilder', endpointName: '/xunit', importFilePath: 'Resultsimport.xml', importToSameExecution: 'true', projectKey: 'XJ', serverInstance: 'CLOUD-3f0b34ae-2880-4013-9571-41ed5f13027f', testExecKey: 'XJ-5', testPlanKey: 'XJ-4'])
	}
    }
	
}
