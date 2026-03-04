pipeline {
    agent any

    triggers {
        githubPush()
    }

    environment {
        XYZ_REPO = 'https://github.com/Akshay9522/Practice.git'
        XYZ_BRANCH = 'master'
    }

    stages {

        stage('Checkout ABC') {
            steps {
                checkout scm
            }
        }

        stage('Clone XYZ Automation') {
            steps {
                dir('xyz-automation') {
                    git branch: "${XYZ_BRANCH}",
                        url: "${XYZ_REPO}"
                }
            }
        }

        stage('Run Automation Tests') {
            steps {
                dir('xyz-automation') {
                    bat 'mvn clean test'
                    // If Linux use:
                    // sh 'mvn clean test'
                }
            }
        }
    }

    post {
        success {
            echo 'Automation executed successfully!'
        }
        failure {
            echo 'Automation failed. Check console logs.'
        }
    }
}
