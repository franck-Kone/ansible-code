pipeline{
    agent any

    stages{
        stage("zip the file") {
            steps{
                sh "zip ansible-${BUILD_ID}.zip * --exclude Jenkinsfile"
                sh 'ls -l'
            }
        }
        stage("upload artifacts to jfrog") {
            steps{
                sh 'curl -uadmin:AP8gcgmmset5jeYChTJYDN6XmDd -T ansible-${BUILD_ID}.zip "http://54.152.4.68:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        }
    }

}