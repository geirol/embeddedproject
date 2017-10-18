pipeline {
      agent {
            docker
            {
                  image 'praqma/native-gradle'
                  args '-v $HOME/.m2:/home/jenkins/.m2 -v $HOME/.gradle:/home/jenkins/.gradle'
            }
      }
      stages {
          stage ('Build') {
              steps {
                  sh "make clean && make all"
                  sh "./gredlew publish"
              }
          }
          stage ('Archive') {
              steps {
                  archiveArtifacts 'build/distributions/*.zip'
              }
          }
      }
}
