pipeline {
    agent {
        label 'node1'
    }
    stages {
        stage('build') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }
        stage('run') {
            steps {
                sh 'python3 app.py &'
            }
        }
        stage('test') {
            steps {
                sh 'slep 60 && curl localhost:8080'
            }
        }
        stage('cleanup') {
            steps {
                sh 'fuser -k 8080/tcp'
            }
        }
    }
}
