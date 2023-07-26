#!/usr/bin/env groovy

@Library('shared-library@master')

pipeline {
  agent any
  
  parameters {
    file 'log.txt'
  }
  
  stages {
    stage('readfile') {
      steps {
        env.WORKSPACE = pwd()
        def filecontent = readFile "${env.WORKSPACE}/log.txt"
        echo $filecontent
      } 
    }

    stage('checklog'){
      steps {
        filterLogs('WARNING', 5)
      }
    }
  }
}
