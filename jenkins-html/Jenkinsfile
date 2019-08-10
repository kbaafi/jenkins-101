pipeline {
    agent any
    stages {
      stage(‘Lint_HTML’) {
        steps {
          sh ‘cd jenkins-html’
          sh ‘tidy -q -e *.html’
        }
      stage(‘Upload_to_AWS’) {
        steps {
          withAWS(region:’us-west-2’,credentials:’blueocean’) {
            s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:’index.html’, bucket:’c3pipelines’)
          }
        }
      }
    }
}