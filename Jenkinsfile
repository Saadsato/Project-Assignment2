pipeline {
      agent any

      tools {
          maven "3.8.7"
      }

      stages {
          stage('package') {
              steps {
                  echo 'packaging...'
                  sh 'mvn war:war -f backend'
                  echo 'packaged'
                  echo 'downloading github project...'
                  git branch: 'main', url: 'https://github.com/Saadsato/Project-Assignment2.git'

              }
          }
           stage('test') {
              steps {
                  echo 'starting test.....'
                  sh 'mvn surefire:test -f backend'
                  echo 'finished test'
              }
          }
      }  
        
      post {
          always {
              echo 'generating test report....'
              junit 'target/*reports/**/*.xml'
              echo 'test report generated'
          }
      }
}