pipeline {
    agent any
    stages {
        stage('Java Check') {
    steps {
        bat 'java -version'
    }
}
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/ValuedZer0/hello-world-java1.git'
            }
        }
        stage('Build') {
            steps { bat 'gradle clean build'}
        }
        stage('Test') {
            steps { bat 'gradle test'}
        }
        stage('Deploy') {
            steps { powershell 'java -jar build/libs/hello-world-java-V1.0.jar'}           
        }    
}

post {
        always {
            echo 'Cleaning up workspace'
            deleteDir() // Clean up the workspace after the build
        }
        success {
            echo 'Build succeeded!!!'
            // You could add notification steps here
        }
        failure {
            echo 'Build failed!'
            // You could add notification steps here
        }
    }
    
}
