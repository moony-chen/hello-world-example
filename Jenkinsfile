pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        withMaven(maven: 'M3', jdk: 'jdk8') {
          sh 'mvn clean install'
        }

      }
    }

    stage('Result') {
      steps {
        archiveArtifacts 'target/*.jar'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }

  }
}