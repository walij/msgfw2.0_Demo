pipeline {  
  agent any
  stages { 
          stage ('SCM Check Out') {
                           steps {
                                   git url: 'https://github.com/walij/msgfw2.0_Demo.git'
                                 }
                          }
          stage ('Test Bed Set Up') { 
                                     steps {
                                             dir('C:\\\\DOCKER\\\\MSGFW2.0')
                                       {
                                         //build docker image "msgfw2.0" with tag "test"
                                         bat label: '', script: 'docker build --pull --target testrunner -t msgfw2.0:test .'
                                       }
                                            }
                                    } 
           stage ('MSGFW2.0 Unit Test Execution') { 
                                 steps {
                                         dir('C:\\\\DOCKER\\\\MSGFW2.0')
                                   {
                                     //Command to run image Container
                                      bat label: '', script: 'docker run --rm -v "C:\\Docker\\MSGFW2.0\\Test Results":C:\\app\\msg.Testframework_cs\\TestResults msgfw2.0:test'
                                   }
                                       }
                                }
                      }

            }
