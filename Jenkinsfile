pipeline {
    agent any

    environment {
        APP_PORT = "8089"
    }

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
                sh '''
                    pkill -f "spring-petclinic" || true
                    nohup java -jar target/spring-petclinic-*.jar --server.port=$APP_PORT > petclinic.log 2>&1 &
                '''
            }
        }

        stage('Verify') {
            steps {
                script {
                    sh '''
                      for i in {1..10}; do
                        curl -s http://localhost:$APP_PORT > /dev/null && exit 0
                        echo "Waiting for app..."
                        sleep 3
                      done
                      echo "App failed to start"
                      exit 1
                    '''
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
