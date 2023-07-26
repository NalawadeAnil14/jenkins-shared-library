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
      }
    }

    stage('Move File to Workspace') {
      steps {
        // Debug: Print the value of FILE_PARAM
        echo "Selected File: ${FILE_PARAM}"


        // Move the selected file from the temporary location to the workspace
        sh 'cp $FILE_PARAM ${WORKSPACE}/'
      }
    }

    stage('readfile') {
      steps {
        script {
          def filecontent = readFile "${WORKSPACE}/$FILE_PARAM"
          echo $filecontent
        }
      }
    }

    stage('check warn') {
      steps {
        script {
          filterLogs('WARNING', 1)
        }
      }
    }
  }
}
