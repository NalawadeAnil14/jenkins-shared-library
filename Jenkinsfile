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
                echo "Selected File: ${params.FILE_PARAM}"

                // Prompt user to select a file using the FILE_PARAM parameter
                input message: 'Select a file', parameters: [file(name: 'FILE_PARAM')]

                // Move the selected file from the temporary location to the workspace
                sh 'cp $FILE_PARAM ${WORKSPACE}/'
            }
        }


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
}
}
}
