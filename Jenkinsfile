def TEST_VAR = "test variable";

def TEST_METHOD() {
    return "test return"
}

node {

     node {
        label 'master'
        customWorkspace "${env.JobPath}"
     }

    environment {
        COMMON_ENV = "common env"
    }

    stages {
        stage('Stage 1') {
            steps {
                echo '${COMMON_ENV}'
                sh('pwd')
            }
        }

        stage('Stage 1') {
            environment {
                LOCAL_ENV = 'local env'
            }
            steps {
                echo '${COMMON_ENV}'
                echo '${LOCAL_ENV}'
            }
        }
    }
}