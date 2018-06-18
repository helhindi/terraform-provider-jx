pipeline {
    agent {
        label "jenkins-go"
    }
    stages {
        stage('CI Build and push snapshot') {
            when {
                branch 'PR-*'
            }
            steps {
                container('go') {
                    sh "make fmt testacc"
                }
            }
        }

        stage('Build and Push Release') {
            when {
                branch 'master'
            }
            steps {
                container('go') {
                    sh "make"
                }
            }
        }
    }
}