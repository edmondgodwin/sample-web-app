pipeline{
    agent any
    environment{
        script_options = "--clean 30"
        Docker_cred = credentials('docker-cred')
    }
    options{
        buildDiscarder(logRotator(numToKeepStr: '5'))
        timestamps()
    }
    stages{
        stage('clone'){
            agent {
                docker {
                    image 'maven'
              }
            }
            environment{
                script_options = "--clean 50"
            }
            steps{
                sh 'mvn --version'
                sh 'printenv'
                sh 'echo $script_options'
            }
        }

        stage('build'){
            agent {
                docker {
                    image 'node'
                }
            }
            options{
                timeout(time: 1, unit: 'MINUTES')
            }
            steps{
                sh 'node --version'
                sh 'printenv'
            }
            post{
                success{
                    sh 'echo build completed'
                }
                aborted{
                    sh 'Stage aborted'
                }
            }
        }

        stage('docker login'){
            steps{
                sh 'docker login -u $Docker_cred_USR -p $Docker_cred_PSW'
            }
        }
    }

    post{
        always{
            cleanWs()
        }
    }
}
