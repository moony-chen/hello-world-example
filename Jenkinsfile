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
    stage('Static Code Analysis'){
      steps {
        withMaven(maven: 'M3', jdk: 'jdk8') {
          sh 'mvn clean verify sonar:sonar -Dsonar.projectName=example-project -Dsonar.projectKey=example-project -Dsonar.projectVersion=$BUILD_NUMBER';
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
