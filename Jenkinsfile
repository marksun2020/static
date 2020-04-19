pipeline {
     agent any
     stages {
          stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
          stage('Upload to AWS') {
              steps {
                  withEnv(["AWS_ACCESS_KEY_ID=${env.AWS_ACCESS_KEY_ID}",
                    "AWS_SECRET_ACCESS_KEY=${env.AWS_SECRET_ACCESS_KEY}",
                    "AWS_DEFAULT_REGION=${env.AWS_DEFAULT_REGION}"]) {
                  sh 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'project3-jenkins-ci-cd')
                  }
              }
         }
     }
}
