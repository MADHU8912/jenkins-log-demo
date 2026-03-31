pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking source code from Git'
            }
        }

        stage('CMD File Check') {
            steps {
                echo 'Listing files using CMD'
                bat 'dir'
            }
        }

        stage('Build Log') {
            steps {
                echo 'Build started'
                bat 'echo Build started at %date% %time% > build.log'
                bat 'echo Build successful >> build.log'
                bat 'type build.log'
            }
        }

        stage('Application Log') {
            steps {
                echo 'Running application script'
                bat 'call app.bat'
            }
        }

        stage('Pipeline Log') {
            steps {
                echo 'Pipeline stage log example'
                echo 'Checkout complete'
                echo 'Build complete'
                echo 'Application execution complete'
            }
        }

        stage('Archive Logs') {
            steps {
                archiveArtifacts artifacts: '*.log', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS'
        }
        failure {
            echo 'Pipeline FAILED'
        }
        always {
            echo 'Build finished. Logs collected.'
        }
    }
}