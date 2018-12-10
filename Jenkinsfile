pipeline {
    agent none

    stages {
        stage('step1') {
            steps {
                node('master') {
                    checkout scm
                    sh('sleep 10; echo "Step 1 done"')
                }
            }
        }
        stage('parallel-demo') {
            steps {
                parallel Step2: {
                    node('master') {
                        checkout scm
                        sh('sleep 10; echo "Step 2 done"')
                    }
                },
                Jenkinsfile: {
                    node('master') {
                        checkout scm
                        sh('cat Jenkinsfile')
                    }
                }
            }
        }
        stage('step3') {
            steps {
                node('master') {
                    sh('sleep 10; echo "Step 3 done"')
                }
            }
        }
    }
}
