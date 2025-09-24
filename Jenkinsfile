pipeline {
   agent any

   stages {
     stage('Checkout') {
       steps {
         // Clone your repo
         git branch: 'main',
             url: 'https://github.com/muahmed471/Spring-Pet-Clinic-Project.git'
       }
     }

     stage('Build') {
       steps {
         echo 'Building the application...'
         // Run Maven inside spring-petclinic folder
         dir('spring-petclinic') {
           sh 'mvn clean package'
         }
       }
     }

     stage('Deploy') {
       steps {
         echo 'Deploying application...'
         // Run the JAR from spring-petclinic/target
         dir('spring-petclinic') {
           sh 'nohup java -jar target/*.jar > app.log 2>&1 &'
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
