pipeline {
     agent any
     stages   {
      stage('Clone Code') { // for display purposes
         // Get some code from a GitHub repository
         git 'https://github.com/mitchewer/github-project-for-jenkins-blueocean.git/'
      }
      stage('Build') {
          sh "mvn clean"
          sh "infer -- mvn compile"
      }
      stage('Testing') {
          sh "mvn test"
          junit 'target/surefire-reports/TEST-*.xml'
      }
      stage('Package') {
          sh "'mvn' -Dmaven.test.skip=true package"
          archive 'target/*.war'
      }
      stage('Deploy') {
          echo 'pipeline success'
      }
    }
 }
