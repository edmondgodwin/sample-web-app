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
        sh 'echo build'
      }
    }
  }
}
