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

 
bat label: '', script: 'cd C:\\DOCKER\\MSGFW2.0'

 
}

 
}

 
stage ('Docker Build') {

 
steps {
bat label: '', script: 'cd C:\\DOCKER\\MSGFW2.0\\msg.Testframework_cs'
 
bat label: '', script: 'docker build -t msgfw2.0 .'

 
}

 
}

 
stage ('Execution') {

 
steps {

 
bat label: '', script: 'docker build --pull --target testrunner -t msgfw2.0:test .'

 
}

 
}

 
stage ('Report') {

 
steps {

 
bat label: '', script: 'docker run --rm -v "C:\\Docker\\TestResults":C:\\app\\msg.Testframework_cs\\TestResults msgfw2.0:test'

 
}

 
}

 
 

 
 

 
}

 
}
