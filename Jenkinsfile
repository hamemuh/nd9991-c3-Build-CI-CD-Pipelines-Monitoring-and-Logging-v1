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
        withAWS(region: 'us-east-2', credentials: 'aws-jenkins') {
          sh 'echo "Uploading content with AWS creds"'
          s3Upload(file: 'index.html', bucket: 'jenkins-udacitiy-bucket')
        }

      }
    }

  }
}
