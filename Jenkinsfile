pipeline {

   agent any

   stages {

      stage('Build') {

         steps {
            sh "./mvnw clean install"
         }

         post {
            success {
               archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
         }
      }

      stage('Test') {

         steps {
            sh "./mvnw test"
         }

         post {
            success {
               junit '**/target/surefire-reports/*.xml'
            }
         }
      }
   }
}

