pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                tidy -q -e *.html
            }
        }
        stage('Upload to AWS') {
            steps {
                sh 'echo "Hello World"'
                sh'''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
                withAWS(region:'eu-central-1',credentials:'aws-static') {
                    s3Upload(file:'index.html', bucket:'lotfy-bucket', path:'index.html')
                }
            }
        }
    }
}