pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''mvn  sonar:sonar \\
  -Dsonar.projectKey=petclinic \\
  -Dsonar.projectName=\'petclinic\' \\
  -Dsonar.host.url=http://13.201.54.4:9000 \\
  -Dsonar.token=sqp_d9b0565f25fcc64dc00987405be6ef28a9bf7ce7'''
      }
    }

    stage('Tests') {
      steps {
        sh './mvnw "-Dtest=**/petclinic/*/*.java" test'
      }
    }

  }
}