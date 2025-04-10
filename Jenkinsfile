pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'your-git-credentials-id', url: 'your-git-repository-url' // Replace with your credentials ID and repository URL
            }
        }
        stage('Build') {
            steps {
                sh './gradlew clean assembleDebug'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew testDebug' // For unit tests
                // To run connected Android tests (UI tests), you might need more setup with the Android Emulator Plugin
                // Example (requires Android Emulator Plugin):
                androidEmulator {
                    avdName 'your_avd_name' // Replace with your AVD name
                    sdkRoot '/path/to/android/sdk' // Replace with your Android SDK path on the Jenkins agent
                    script {
                        sh './gradlew connectedCheck'
                    }
                }
            }
        }
    }
}