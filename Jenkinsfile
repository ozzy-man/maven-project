pipeline {
  agent any
  triggers {
    pollSCM('*/5 * * * *')
  }
  stages {
    stage ('Build'){
      steps {
        bat 'mvn clean package'
      }
      post {
        success {
          echo 'Archiving...'
          archiveArtifacts artifacts:'**/target/*.war'
        }
      }
    }
    stage ('Deployments'){
      parallel {
        stage ('Deploy to Staging'){
          steps {
            bat 'copy webapp\\target\\*.war "C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps" /Y'
          }
        }
        stage ('Deploy to prod'){
          steps {
            bat 'copy webapp\\target\\*.war "C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0_Product\\webapps" /Y'
          }
        }
      }
    }
  }
}