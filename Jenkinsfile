pipeline {
   agent any

   tools {
      maven "maven-3.6.3"
   }
  options {
        skipStagesAfterUnstable()
    }
    stages {
      stage('compile'){
        steps{
          git 'https://github.com/shiv5454/springboot_swagger.git'
        }
      }
         
      stage('Build') {
         steps {
             bat "mvn -Dmaven.test.failure.ignore=true clean package"
         }

         post {
            success {
               junit '**/target/surefire-reports/TEST-*.xml'
               archiveArtifacts 'target/*.jar'
            }
         }
      }
      
     stage('test'){
      steps{
        bat "mvn -Dmaven.test.failure.ignore=true test"
      }
    }
   }
}
