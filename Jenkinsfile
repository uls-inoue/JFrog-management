pipeline {
  // todo agentをカブコム環境にあわせwindowsを指定するようにする
  agent any
  environment {
    LogLevel = 'normal'
  }
  tools {
    jfrog 'jfrog-cli'
  }
  options {
    // numToKeepStr: ビルドログを残す個数、artifactNumToKeepStr: ビルド成果物を残す個数
    buildDiscarder(logRotator(numToKeepStr: '50', artifactNumToKeepStr: '10'))
  }
  stages {
    stage("CreateJFrogRespository"){
      steps{
        script {
          def TARGET_ENV = "${params.TARGET_ENV}".tokenize('\n')
          echo "${params.REPOSITORY_KEY}"
          echo "${TARGET_ENV}"
          for (i in "${params.TARGET_ENV}"){
            echo "${i}"
          }
                    // for (i = 0; i < "${TARGET_ENV}.length"; i++ ){
          //   echo "${TARGET[i]}"
          // }
          echo "${TARGET_ENV[0]}"
          // jf 'rt repo-create template.json --vars="project=kabucom-devel;repository=${params.REPOSITORY_KEY};environment=${ENV}"'
        }
      }
    }
  }
}
