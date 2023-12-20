pipeline {
  // todo agentをカブコム環境にあわせwindowsを指定するようにする
  agent any
  environment {
    LogLevel = 'normal'
    JFrogServerID = 'kabucom-jfrog'
    JFrogRepositoryKey = 'kabucom-release-'
    JFrogModuleName = 'Kabucom'
    // todo ビルド名を本利用のものにかえる
    JFrogBuildName = 'kabucom-releasetest-build'
  }
  tools {
    jfrog 'jfrog-cli'
  }
  options {
    // numToKeepStr: ビルドログを残す個数、artifactNumToKeepStr: ビルド成果物を残す個数
    buildDiscarder(logRotator(numToKeepStr: '50', artifactNumToKeepStr: '10'))
  }
  stages {
    stage("UploadToJFrog"){
      steps{
        script {
          jf '--version'
          // todo
          // ・ReleaseDateを外部から指定できるようにする
          // ・リリース先環境名を外部から指定できるようにする
          // ・依存に追加するリポジトリを外部から指定できるようにする
          // def ReleaseDate = '20231208'
          // def JFrogTarget = env.JfrogRepositoryKey + 'releasetest/' + ReleaseDate + '/'
          // withEnv(['JFrogTarget='+JFrogTarget, 'JFROG_CLI_BUILD_NAME=' + JFrogBuildName, 'JFROG_CLI_BUILD_NUMBER='+ env.BUILD_ID]) {
          //   // なにかひとつファイルをアップロードしないとbadが+bprできないので、releaseinfo.jsonをアップロードしておく
          //   jf 'rt u ./releaseinfo.json ${JFrogTarget} --module=${JFrogModuleName}'
          //   // リリース対象物の一括ダウンロードと一括差分チェックができるよう、add-dependenciesコマンドで複数のリポジトリ内のリリース対象物をまとめる。
          //   jf 'rt bad ${JFrogBuildName} ${BUILD_NUMBER} kabucom-kisaragi-extlib-TA-Cooperation-Dev/1.0.0/Cooperation.dll --from-rt --module=TA'
          //   jf 'rt bad ${JFrogBuildName} ${BUILD_NUMBER} kabucom-KisaragiProjects.Kisaragi-Feature/feature/develop-jfrog-artifact/uls-ito/35/* --from-rt --module=Kisaragi'
          //   jf 'rt bad ${JFrogBuildName} ${BUILD_NUMBER} kabucom-kisaragi-extlib-TA-NetLib.Ose-Dev/1.0.0/NetLib.Ose.dll --from-rt --module=TA'
          //   jf 'rt bce'
          //   jf 'rt bag'
          //   jf 'rt bp'
          //   //リリース対象物を一括でダウンロードできるよう、リリースリポジトリにリリース対象物をプロモートする
          //   jf 'rt bpr ${JfrogBuildName} ${BUILD_NUMBER} kabucom-release-releasetest --copy --include-dependencies'
          // }
        }
      }
    }
  }
}
