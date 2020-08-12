pipeline {
  agent any
  stages {
    stage('LINT HTML') {
      steps {
        sh 'tidy -q -e *.html'
      }
    }
    stage('Upload to AWS') {
      steps {
           withAWS(region:'us-east-2', credentials:'aws-static') {
            sh 'echo "Uploading content with AWS credentials to s3 bucket"'
            s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'jenkins-project3-udacity-konrad')
        }
      }
    }
  }
}
