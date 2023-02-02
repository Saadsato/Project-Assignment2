pipeline {
    
    agent any

    tools {
       
        maven "3.8.7"
    }

    stages {
        stage('clean and checkout') {
            steps {
                sh 'mvn clean -f backend'
                echo 'downloading github project...'
                git branch: 'main', url: 'https://github.com/Saadsato/Project-Assignment2.git'
                
            }
        }

        stage('build') {
            steps {
                echo 'building...'
                sh 'mvn test-compile -f backend'
                echo 'finished building'
            }
        }

        stage('test') {
            steps {
                echo 'starting test.....'
                sh 'mvn surefire:test -f backend'
                echo 'finished test'
            }
        }

        stage('package') {
            steps {
                echo 'packaging...'
                sh 'mvn war:war -f backend'
                echo 'packaged'
            }
        }
        stage('deploy') {
            steps {
                dir('./backend'){
                    sh 'pwd'
                    sh 'cp ./target/ROOT.war /artifacts'
                }
            }
        }
    }
    post {
        always {
            dir('./backend'){
                echo 'generating test report....'
                junit 'target/*reports/**/*.xml'
                echo 'test report generated'
            }
        }
    }
}