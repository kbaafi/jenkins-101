pipeline {
  agent any
  stages {
    stage('Lint-HTML') {
      steps {
        sh '''cd jenkins-html && tidy -q -e *.html'''
      }
    }
    stage('Upload-to-AWS') {
      steps {
        withAWS(region:'eu-north-1',credentials:'jenkins-aws') {
          s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'jenkins-html/index.html', bucket:'kb-uda-dend')
        }
      }
    }
  }
}