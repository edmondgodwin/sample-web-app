pipeline{
  agent any
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

      steps{
        sh 'echo build'
      }
    }

    stage('build'){
      steps{
        sh 'echo build'
      }
    }
  }
}
