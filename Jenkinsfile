#!/usr/bin/env groovy

@Library('shared-library@master') _

pipeline {
  agent any

  parameters {
    file(name: 'FILE_PARAM', description: 'Select a file to use')
  }

  stages {
    stage('Checkout') {
      steps {
        // Checkout the repository to get the Jenkinsfile in the workspace
        checkout scm
        echo "Selected File: ${FILE_PARAM}"
      }
    }

    stage('readfile') {
      steps {
        script {
          def filecontent = readFile "${WORKSPACE}/$FILE_PARAM"
          echo "${filecontent}"
        }
      }
    }

    stage('check warn') {
      steps {
        script {
          filterLogs('Warning', 1)
        }
      }
    }
  }
}
