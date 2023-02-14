pipeline{
    agent {
        docker {
            image 'maven'
        }
    }
    stages{
        stage('clone'){
            steps{
                sh 'mvn --version'
            }
        }

        stage('build'){
            steps{
                sh 'echo build'
            }
        }
    }
}
