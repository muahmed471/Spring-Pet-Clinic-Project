pipeline {
   agent any

   stages {
     stage('Checkout'){
       steps {
         // Clone your repo
         git branch: 'master',
            url: 'https://github.com/muahmed471/Spring-Pet-Clinic-Project.git'
       }
     } 
   
     stage('Build'){
       steps {
         echo 'Building the application...'
         // Using Maven build
         sh 'sudo mvn clean package'
       }
     }
 
     stage('Deploy'){
       steps {
         echo 'Deploying application...'
         // Command to build code
         sh 'sudo java -jar target/*.jar &'
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
