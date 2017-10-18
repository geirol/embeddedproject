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
                  sh "make test"
              }
          }
          stage ('Publish test') {
              steps {
                  junit 'out/bin/results_junit.xml'
              }
          }
          stage ('Archive') {
              steps {
                  archiveArtifacts 'out/bin/main'
              }
          }
      }
}
