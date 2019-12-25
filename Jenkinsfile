def TEST_VAR = "test variable";

def TEST_METHOD() {
    return "test return"
}

pipeline {

    agent any

    environment {
        COMMON_ENV = "common env"
    }

    stages {
        stage('Stage 1') {
            steps {
                echo '${COMMON_ENV}' + COMMON_ENV
                sh('pwd')
            }
        }

        stage('Stage 2') {
            environment {
                LOCAL_ENV = 'local env'
            }
            steps {
                echo '${COMMON_ENV}' + COMMON_ENV
                echo '${LOCAL_ENV}' + LOCAL_ENV
            }
        }

        stage('Stage 3') {
            withEnv(['aaa=bbb', 'bbb=ccc', 'ccc=ddd', 'eee=${COMMON_ENV}']) {
                echo '${aaa}'
                echo '${bbb}'
                echo '${ccc}'
                echo '${eee}'
            }
        }
    }
}