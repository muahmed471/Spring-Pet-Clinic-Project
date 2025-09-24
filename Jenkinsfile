pipeline {
   agent any

   stages {
     stage('Checkout'){
       steps {
         // Clone your repo
         git branch: 'main',
            url: 'https://github.com/muahmed471/Spring-Pet-Clinic-Project.git'
       }
     } 
   
     stage('Build'){
       steps {
         echo 'Building the application...'
         // Using Maven build
         dir('spring-petclinic') {
         sh 'mvn clean package'
       }
     }
   }
     stage('Deploy'){
       steps {
         echo 'Deploying application...'
         // Command to build code
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
