pipeline{
    agent any
    stages {
        stage("test echo") {
            steps{
                sh "echo successfully passed"
            }
        }
    }

     stages{
        stage("zip the file") {
            steps{
                sh 'rm -rf *.zip || echo "No files with .zip extension found"'
                sh "zip -r ansible-${BUILD_ID}.zip * --exclude Jenkinsfile"
                sh 'ls -l'
            }
        } 
        /*
        stage("upload artifacts to jfrog") {
            steps{
                sh 'curl -uadmin:AP8gcgmmset5jeYChTJYDN6XmDd -T ansible-${BUILD_ID}.zip "http://100.26.177.95:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        } 
        stage('Publish to ansible server') {
            steps{
               sshPublisher(publishers: [sshPublisherDesc(configName: 'Ansible server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'unzip -o ansible-${BUILD_ID}.zip; rm -rf ansible-${BUILD_ID}.zip', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'ansible-${BUILD_ID}.zip')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        } 
    } */
}
