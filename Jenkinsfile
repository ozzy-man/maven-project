pipeline {
  agent any
  stages {
    stage ('Build'){
      steps {
        cmd 'mvn clean package'
      }
      post {
        success {
          echo 'Archiving...'
          archiveArtifacts artifacts:'**/target/*.war'
        }
      }
    }
    stage ('Compile'){
      steps {
        echo "Compile step..."
      }
    }
    stage ('Deploy'){
      steps {
        echo "Deploy step..."
      }
    }
  }
}