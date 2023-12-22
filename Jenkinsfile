pipeline {
  agent any
  stages {
    stage("test"){
      steps{
        script {
          echo "${env.BRANCH_NAME}"
        }
      }
    }
  }
}
