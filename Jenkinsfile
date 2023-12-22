pipeline {
  agent any
  stages {
    stage("test"){
      steps{
        script {
          echo "${env.CHANGE_TARGET}"
        }
      }
    }
  }
}
