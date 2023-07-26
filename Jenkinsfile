#!/usr/bin/env groovy

@Library('shared-library@master') _

pipeline {
  agent any
  
  parameters {
    file (name: 'INPUT_FILE')
  }
  
  stages {
    stage('readfile') {
      steps {
        script {
          sh 'cp $INPUT_FILE ${WORKSPACE}'
          def filecontent = readFile "${WORKSPACE}/log.txt"
          echo $filecontent
        }
      } 
    }

    stage('checklog'){
      steps {
        filterLogs('WARNING', 5)
      }
    }
  }
}
