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
    }ß  
    stage('build'){
      steps{
        sh 'echo build'
      }
    }
  }
}
