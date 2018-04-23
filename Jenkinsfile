 pipeline {
    agent any
    stages   {
      stage('Checkout') {
        steps {
            git 'https://github.com/mitchewer/github-project-for-jenkins-blueocean.git/', branch: 'master'
            echo 'Get some code from a GitHub repository'
        }
      }
      stage('Build') {
        steps {
            echo 'starting deploy to......'
		    sh 'mvn -B clean install'
        }
      }
      stage('Testing') {
        steps {
            sh "mvn test"
            junit 'target/surefire-reports/TEST-*.xml'
        }
      }
      stage('Package') {
        steps {
            sh "'mvn' -Dmaven.test.skip=true package"
            archive 'target/*.war'
        }
      }
      stage('Deploy') {
        steps {
            echo 'pipeline success'
        }
      }
    }
 }
