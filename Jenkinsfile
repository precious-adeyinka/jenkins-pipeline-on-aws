pipeline {

  agent any

  stages {

    stage('Build') {
      steps {
        sh 'echo "Jenkins Pipeline on AWS Project"'
        sh 'echo "Author: Precious Adeyinka"'
        sh '''
         echo "Get Directory Listing..."
         ls -lah
        '''
      }
    }

    stage('Lint HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }

    stage('Upload to AWS') {
      steps {
        withAWS(region:'us-west-2', credentials:'aws-static') {
        sh 'echo "Uploading content with AWS creds"'
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'pflash-jenkins-static-bucket')
        }
      }
    } 
  }
}