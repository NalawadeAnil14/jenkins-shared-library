pipeline {
  agent any

  parameters {
    file 'log.txt'
    file (name: 'INPUT_FILE')
  }

  stages {
    stage('readfile') {
      steps {
        script {
          env.WORKSPACE = pwd()
          def filecontent = readFile "${env.WORKSPACE}/log.txt"
          sh 'cp $INPUT_FILE ${WORKSPACE}'
          def filecontent = readFile "${WORKSPACE}/log.txt"
          echo $filecontent
        }
      } 
