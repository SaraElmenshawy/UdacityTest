pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                bat 'echo "Hello World"'
                 bat '''
                     echo "Multiline shell steps works too"
                 '''
             }
         }
          stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-east-1',credentials:'selmensh_p') {
                  bat 'echo "Uploading content with AWS creds"'
                      s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'selmensh')
                  }
              }
         }
     }
}
