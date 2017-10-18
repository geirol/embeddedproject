pipeline {
      agent {
            docker
            {
                  image 'Dockerfile'
                  args '-v $HOME/.m2:/home/jenkins/.m2'
                  args '-v $HOME/.gradle:/home/jenkins/.gradle'
            }
      }
      stages {
          stage ('Build') {
              steps {
                  sh "make clean && make all"
                  sh "./gredlew publishToMavenLocal"
              }
          }
          stage ('Archive') {
              steps {
                  archiveArtifacts 'build/distributions/*.zip'
              }
          }
      }
}
