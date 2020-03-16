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

	tage('Deploy') {
      when {
        expression { env.BRANCH_NAME == 'master' }
      }
      steps {
        sh 'mvn deploy'
      }
    }

  }
}