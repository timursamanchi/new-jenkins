pipeline {
    agent any
    // this a line of comment

    parameters {
        string ( name: 'VERSION',
            defaultValue: 'xx.x.x',
            description: 'Enter version to upgrade.'
        )
        
        booleanParam ( name: 'RUN_TEST',
            defaultValue: false,
            description: 'Toggle this value to run the tests'
        )

        text ( name: 'REASONS',
            defaultValue: 'Start of Refresh Cycle, spoke to John from IT,...lablablabla',
            description: 'Enter reasons for upgrade'
        )

        choice ( name: 'AWS_REGION',
            choices: ['EAST','WEST','NORTH','SOUTH',],
            description: 'Select deployment region.'
        )

        choice ( name: 'ENVIRONMENT',
            choices: ['DEV','PROD','STAGING'],
            description: 'Enter enviroment name for depolyment.'

        )

        password ( name: 'DB2_PASSWORD',
            defaultValue: 'f1234452345344564345645634',
            description: 'Enter Db2 password.'
        )
    }

    environment {
        MY_STR = 'Hi this is Timur...'
        MAX_SIZE = 10
        MIN_SIZE = 100
    }

    stages {
        stage ('TESTING') {
            steps {
                echo 'hello world',
                sh 'echo "this is a report" > new-jenkins-pipeline-report.txt'
            }
        }
        stage ('INSTALLING') {
            steps {
                echo "you know ${MY_STR}"
            }
        }
        stage ('Deploy to non-production environment') {
            when {
                // only deploy if environment is not PROD
                expression {
                    params.ENVIRONMENT != 'PROD'
                }
            }
            steps {
                echo "Deploying to ${params.ENVIRONMENT}"
            }
        }
        stage ('Deploy to production') {
            // only deploy to PROD
            when {
                expression {
                    params.ENVIRONMENT == 'PROD'
                }
            }
            steps {
                input message 'Confirm Deployment to PROD...', ok: 'Deploy'
                echo "Deploying to ${params.ENVIRONMENT}, manual approval required"
                
            }
        }
        stage ('STAGING') {
            steps {
                echo "deploying to ${params.AWS_REGION}"
            }
        }

        stage ('Report') {
            steps {
                sh 'echo "this is another line in the report" >> new-jenkins-pipeline-report.txt'
                echo "build duration: ${currentBuild.duration}"

            }
        }
        stage ('post') {
            steps {
                echo "Build ID: ${BUILD_ID}"
                echo "Results: ${currentBuild.currentResult}"
                echo "RUN the tests?: ${params.RUN_TEST}"

                sh 'echo "Build ID: ${BUILD_ID}" >> new-jenkins-pipeline-report.txt'
                sh 'echo "Deploying to ${params.ENVIRONMENT}" >> new-jenkins-pipeline-report.txt

                archiveArtifacts allowEmptyArchive: true, artifacts: '*.txt', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
            }
        }
    }
}
