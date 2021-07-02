pipeline {
  agent any
  stages {
    stage('CodeCollection') {
      steps {
        git(url: 'https://github.com/srivaniKammari/bookzy-bookstore.git', changelog: true, poll: true, branch: 'master')
      }
    }

     stage("Maven Build"){
       steps{
            sh "mvn clean package"
            sh "mv target/*.war target/mywebapp.war"
             }
            }
            
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }

    stage('ReportPublish') {
      steps {
        junit 'target/surefire-reports/*.xml'
      }
    }

  }
}

