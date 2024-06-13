pipeline {
    agent any
    stages {
        stage ('clean') {
            steps {
                cleanWs()
            }
        }
        stage ('Run Script') {
            steps {
                sh "sh run.sh"
            }
        }
        stage ('Generate Artifacts') {
            steps {
                sh '''
                #!/bin/bash
                for i in {1..5}; do echo "This is file \$i" > file\$i.txt; done
                '''
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: '*.txt', followSymlinks: false
        }
    }
}