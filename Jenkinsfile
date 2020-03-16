pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean'
      }
    }

    stage('Test') {
      steps {
		sh 'mvn spring-javaformat:apply'
        sh 'mvn test'
      }
    }
	
	stage('Package') {
		steps {
			sh 'mvn package'
		}
	}

	stage('Deploy') {
      when {
        expression { env.BRANCH_NAME == 'master' }
      }
      steps {
        sh 'mvn clean deploy releaseRepository::default::https://github.com/KhangZhengNg/spring-petclinic'
      }
    }

  }
}