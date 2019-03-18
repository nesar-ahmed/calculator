pipeline {
    agent any
    stages {
        stage('SCM Checkout'){
            git 'https://github.com/nesar-ahmed/calculator'
        }
        stage('Compile Package'){
            sh 'mvn package'
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}
