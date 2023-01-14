pipeline {
    agent any
    tools {
    maven 'maven'
    }
    stages {
        stage ('Clone') {
            steps {
                git 'https://github.com/4ndrevv/gilded-rose-jenkin.git'
                }
            }
        stage('Test') {
            steps {
                echo 'Testing..'
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/4ndrevv/gilded-rose-jenkin.git']])
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
            }
        stage('Deploy') {
            steps {
                 echo 'Deploying....'
                 }
            }
        }
        post {
            always {
                junit(
                    allowEmptyResults:true,
                    testResults: 'test-report/.xml' )}
        }
    }