pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Dependency Check') {
            steps {
                sh '''
                dependency-check \
                  --project Test \
                  --scan . \
                  --out . \
                  --format HTML \
                  --format XML
                '''
            }
        }
    }

    post {
        always {
            dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
        }
    }
}
