pipeline {
  agent any
  tools {
    maven 'Maven' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat8(credentialsId: 'tomcat_user', path: '', url: 'http://ec2-13-57-59-36.us-west-1.compute.amazonaws.com:8080/')], contextPath: '', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
