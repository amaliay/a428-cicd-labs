node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000'){
        stage('Build') {
            sh 'npm install'
        }
        stage('Test') {
            sh './jenkins/scripts/test.sh'
        }
        stage('Manual Approval') {
            input message: 'Lanjutkan ke tahap Deploy?'
        }
        stage('Deploy')
            sh './jenkins/scripts/deliver.sh'
            sleep 60 
            sh 'ssh "./jenkins/scripts/kill.sh'
            echo "Eksekusi pipeline sukses"
        }
    }
}