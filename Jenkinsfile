pipeline {
  agent any
  triggers {
    // Gitのタグ作成をトリガーに設定する
    git(tag: true)
  }
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
