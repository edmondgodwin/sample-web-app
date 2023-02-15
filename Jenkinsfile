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
            
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps{
                sh 'mvn --version'
                sh 'printenv'
                sh 'echo $script_options'
            }
        }

        stage('build'){
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

        stage('Parallel'){
            parallel{
                stage('docker build'){
                    steps{
                        sh 'echo docker build'
                    }
                }
                stage('docker build'){
                    steps{
                        sh 'echo docker build'
                    }
                }
        
            }
        }
    post{
        always{
            cleanWs()
        }
    }
}