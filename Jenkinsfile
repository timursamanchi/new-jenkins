pipeline {
    agent any
    // this a line of comment

    parameters {
        string ( name: 'version',
            defaultValue: 'xx.x.x',
            description: 'Enter version to upgrade.'
        )
        
        booleanParam ( name: 'RUN TEST',
            defaultValue: false,
            description: 'Toggle this value to run the tests'
        )

        text ( name: 'reasons',
            defaultValue: 'Start of Refresh Cycle, spoke to John from IT,...lablablabla',
            description: 'Enter reasons for upgrade'
        )

        choice ( name: 'AWS_REGION',
            choices: ['EAST','WEST','NORTH','SOUTH',],
            description: 'Select deployment region.'
        )
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
