pipeline {
    agent any
    // this a line of comment

    parameters {
        string ( name: 'version',
            defaultValue: 'xx.x.x',
            description: 'Enter version to upgrade.')
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
                echo "build duration: ${currentBuild.duration}"
            }
        }
        stage ('post') {
            steps {
                echo "Build ID: ${BUILD_ID}"
                echo "Results: ${currentBuild.currentResult}"
                sh 'echo "Build ID: ${BUILD_ID}" >> new-jenkins-pipeline-report.txt'
                archiveArtifacts allowEmptyArchive: true, artifacts: '*.txt', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
            }
        }
    }
}
