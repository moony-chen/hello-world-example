pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        tool(name: 'jdk', type: 'jdk8')
        withMaven(maven: 'M3') {
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