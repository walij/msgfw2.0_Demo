pipeline {  
  agent any
  stages { 
          stage ('Clone') {
                           steps {
                                   git url: 'https://github.com/walij/msgfw2.0_Demo.git'
                           }
           }

 
stage ('Initital Setup') { 
steps {
        dir('C:\\\\DOCKER\\\\MSGFW2.0') {
           bat label: '', script: 'docker build --pull --target testrunner -t msgfw2.0:test .'
}
 

           }
           }
  

 
 
stage ('Execution') {

 
steps {

  dir('C:\\\\DOCKER\\\\MSGFW2.0')
bat label: '', script: 'docker run --rm -v "C:\\Docker\\MSGFW2.0\\Test Results":C:\\app\\msg.Testframework_cs\\TestResults msgfw2.0:test'

 
}

 
}

 
}

 
}
