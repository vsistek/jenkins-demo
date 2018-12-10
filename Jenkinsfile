pipeline {
    agent none

    triggers {
        cron('*/5 * * * *')
    }

    stages {
        stage('step1') {
            steps {
                node('master') {
                    checkout scm
                    sh('sleep 10; echo step1')
                }
            }
        }
        stage('parallel-demo') {
            steps {
                parallel Step2: {
                    node('master') {
                        checkout scm
                        sh('sleep 10; echo step2')
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
                    sh('sleep 10; echo step3')
                }
            }
        }
    }
}
