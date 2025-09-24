pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/muahmed471/Spring-Pet-Clinic-Project.git',
                    branch: 'main'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh './mvnw clean package'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'java -jar target/*.jar &'
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
