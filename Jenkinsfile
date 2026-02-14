pipeline {
    agent any

    triggers {
        cron('H/2 * * * *')              // Build periodically every 2 minutes
        pollSCM('H/1 * * * *')           // Poll SCM every 1 minute
    }

    stages {

        stage('Clone Repository') {
            steps {
                echo 'Cloning Repository...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Project...'
                sh 'javac App.java'
            }
        }

        stage('Echo Build Status') {
            steps {
                echo "Build Status: SUCCESS"
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '*.class', fingerprint: true
            }
        }
    }
}
