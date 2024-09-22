pipeline {
    agent any

    parameters {


    }

    environment {
        MY_STR = 'Hi this is Timur...'
        MAX_SIZE = 10
        MIN_SIZE = 100
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
                echo "build duration: ${currentBuild.duration}"
                sh 'echo "Build ID: ${BUILD_ID}" >> new-jenkins-pipeline-report.txt'
                sh 'echo "Duration: ${currentBuild.duration}" >> new-jenkins-pipeline-report.txt'
                archiveArtifacts allowEmptyArchive: true, artifacts: '*.txt', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
            }
        }
    }
}
