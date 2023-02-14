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
    } 
    stage('build'){
      steps{
        sh 'echo build'
      }
    }
  }
}
