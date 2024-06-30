pipeline{
    agent any
    stages {
        stage("test echo") {
            steps{
                sh "echo successfully passed"
            }
        }
        
        stage("zip the file") {
            steps{
                sh 'rm -rf *.zip || echo "No files with .zip extension found"'
                sh "zip -r ansible-${BUILD_ID}.zip * --exclude Jenkinsfile"
                sh 'ls -l'
            }
        }
        stage("Copy file to ansible server") {
            steps{
                sh 'whoami && pwd'
                sh 'scp /var/lib/jenkins/workspace/CI-CD-pipeline/ansible-${BUILD_ID}.zip root@66.228.39.149:/root'
            }
        }
     
        /*
        stage("upload artifacts to jfrog") {
            steps{
                sh 'curl -uadmin:AP8gcgmmset5jeYChTJYDN6XmDd -T ansible-${BUILD_ID}.zip "http://100.26.177.95:8081/artifactory/ansible/ansible-${BUILD_ID}.zip"'
            }
        } */
        stage('Publish to ansible server') {
            steps{
               sh 'ssh root@66.228.39.149 unzip -o ansible-${BUILD_ID}.zip && rm -rf ansible-*.zip'
            }
        } 
        stage('run playbook') {
            steps{
               sh 'ssh root@66.228.39.149 ansible all -m ping'
               sh 'ssh root@66.228.39.149 ansible-playbook play0.yml'
            }
        } 
    
    } 
}
