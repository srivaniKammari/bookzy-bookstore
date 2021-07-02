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
stage('deploy to tomcat') {
      steps {
      deploy adapters: [tomcat8(credentialsId: '3939ec90-51d0-4cc6-bd33-d499e375dc03', path: '', 
      url: 'http://localhost:8080')], contextPath: 'myweb', war: '**/*.war'

     }
    }
  }
}

