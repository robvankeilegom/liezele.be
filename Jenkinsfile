pipeline {
    agent none

    options {
        skipDefaultCheckout(true)
        disableConcurrentBuilds()
    }

    stages {
        stage('Cleanup and Checkout') {
            agent any

            steps {
                cleanWs()

                checkout([
                    $class: 'GitSCM',
                    branches: scm.branches,
                    extensions: [
                        [$class: 'SubmoduleOption', recursiveSubmodules: true]
                    ],
                    userRemoteConfigs: scm.userRemoteConfigs
                ])
            }
        }

        stage('Build site') {
            agent {
                docker {
                    image 'robvankeilegom/golang-hugo'
                }
            }
            steps {
                sh '''
                    hugo
                '''
            }
        }

        stage('Deploy site') {
            agent any
            environment {
                SSH_PORT = credentials('SSH_PORT_ROBVANKEILEGOM_BE')
            }
            steps {
                sshagent(credentials: ['SSH_JENKINS_BOX']) {
                    sh '''
                        rsync -av -e "ssh -p $SSH_PORT" ./public/ rob@liezele.be:~/websites/liezele.be/current --delete
                    '''
                }
            }
        }
    }
}

