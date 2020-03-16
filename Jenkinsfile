pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './mvnw spring-javaformat:apply'
        sh './mvnw package'
      }
    }

    stage('Test') {
      steps {
        sh './mvnw test'
      }
    }

	stage('Deploy') {
      when {
        branch 'master'
      }
      steps {
        sh './mvnw deploy'
      }
    }

  }
}