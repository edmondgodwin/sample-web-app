pipeline{
    agent none
    stages{
        stage('clone'){
            agent {
              docker {
                image 'maven'
            }
            }
            steps{
                sh 'mvn --version'
            }
        }

        stage('build'){
            agent {
              docker {
                image 'node'
            }
            }
            steps{
                sh 'node --version'
            }
        }
    }
}
