pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World"'
        sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
      }
    }

    stage('Upload to AWS') {
      steps {
        withAWS(region: 'us-east-2', credentials: 'aTbfaXWpdG2KmLTvba7l+86Sy1ClHmU3Q0jiRslX') {
          sh 'echo "Uploading content with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file: 'index.html', bucket: 'static-jenkins-pipeline')
        }

      }
    }

  }
}
