pipeline {
    agent any

    environment {
        MY_STR = 'Hi this is Timur...'
    }

    stages {
        stage ('testing') {
            steps {
                echo 'hello world'
            }
        }
        stage ('install') {
            steps {
                echo "you know ${MY_STR}"
            }
        }
        stage ('Report') {
            steps {
                sh 'echo "this is a report" > new-jenkins-pipeline-report.txt'
            }
        }
        stage ('post') {
            steps {
                echo "Build ID: ${BUILD_ID}"
                sh 'echo "Build ID: ${BUILD_ID}" >> new-jenkins-pipeline-report.txt'
            }
        }
    }
}
