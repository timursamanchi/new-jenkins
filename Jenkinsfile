pipeline {
    agent any

    environment {
        MY_STR = 'this is Timur'
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
        stage ('post') {
            steps {
                echo "biuld id: ${BUILD_ID}"
            }

        }
    }
}