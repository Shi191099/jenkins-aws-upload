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
                  withAWS(credentials: 'aws-credentials', endpointUrl: 'https://s3.ap-southeast-2.amazonaws.com', region: 'ap-southeast-2') {
                       sh 'echo "Uploading content with AWS creds"'
                       s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'app.py', bucket:'ozsydney')
                  }
              }
         }
     }
}
