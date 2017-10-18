pipeline {
      agent {
            docker
            {
                  image 'praqma/native-gradle'
                  args '-v $HOME/.m2:/home/jenkins/.m2 -v $HOME/.gradle:/home/jenkins/.gradle'
            }
      }
      stages {
          stage ('IncrementVersion') {
              steps {
                  sh "./gradlew incrementVersion"
              }
          }
          stage ('Build') {
              steps {
                  sh "./gradlew publish"
              }
          }
          stage ('Archive') {
              steps {
                  archiveArtifacts 'build/distributions/*.zip'
              }
          }
      }
}
