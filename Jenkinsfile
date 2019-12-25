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
            steps {
                withEnv(["aaa=bbb", "bbb=ccc", "ccc=ddd", "eee=${COMMON_ENV}"]) {
                    println "${aaa}"
                    println "${bbb}"
                    println "${ccc}"
                    println '${eee}'
                }
            }
        }

        stage('Stage 4') {
            steps {
                checkout scm
            }
        }

        stage('Stage 5') {
            steps {
                sh 'mkdir -p plan-generator'
                withEnv(['gitUrl=https://github.com/mareeskannanr/plan-generator.git'])
                dir('plan-generator') {
                    checkout resolveScm(source: git('${gitUrl}'), targets: [BRANCH_NAME, 'master'])
                }

                sh 'cd plan-generator/'
                sh 'mvn clean install'
                println '***********************'
            }
        }
    }
}