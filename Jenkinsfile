pipeline {
  agent any
  tools {
    maven 'maven' 
  }
  triggers {
    pollSCM '* * * * *'
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://16.16.212.204:8080/')], contextPath: '/springfolder', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
