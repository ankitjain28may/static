pipeline {
    agent any
    stages {
        stage("Upload to AWS") {
            steps {
                withAWS(region:'ap-south-1', credentials:'aws-static') {
                    sh 'echo "Uploading content with AWS creds"'
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'static-site-jenkins-2k20')
                }
             }
        }
    }
}