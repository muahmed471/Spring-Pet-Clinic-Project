pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone repo with submodules
                git url: 'https://github.com/muahmed471/Spring-Pet-Clinic-Project.git',
                    branch: 'main',
                    changelog: false,
                    poll: false
                // Init submodules
                sh 'git submodule update --init --recursive'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                dir('spring-petclinic') {
                    sh 'mvn clean package'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                dir('spring-petclinic') {
                    sh 'java -jar target/*.jar &'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed Successfully'
        }
        failure {
            echo 'Pipeline failed'
        }
    }
}
