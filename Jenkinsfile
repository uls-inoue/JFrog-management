pipeline {
  environment {
  }
  tools {
    jfrog 'jfrog-cli'
  }
  options {
    // numToKeepStr: ビルドログを残す個数、artifactNumToKeepStr: ビルド成果物を残す個数
    buildDiscarder(logRotator(numToKeepStr: '50', artifactNumToKeepStr: '10'))
  }
  stages {
    stage("Build") {
      steps {
        script {
          echo "${env.BRANCH_NAME}"
        }
      }
    }
  }
  post {
    always {
	    powershell "if(Test-Path drop){ Remove-Item -Path drop -Recurse -Force }"
    }
    success {
      rocketSend ":white_check_mark:ビルド完了"
    }
    failure {
      rocketSend ":negative_squared_cross_mark:ビルド失敗"
    }
  }
}
