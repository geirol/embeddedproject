pipeline {
      agent {
            docker { image 'node:praqma/native-make' }
      }
      stages {
          stage ('Pull code') {
              steps {
                  git 'https://github.com/geirol/embeddedproject.git/'
              }
          }
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
