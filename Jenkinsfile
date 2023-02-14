pipeline{
  agent 
  stages{
    stage('clone'){
      agent{
        docker{
          image 'maven'
        }
      }
      steps{
        sh 'echo build'
      }
    }
  }
}
