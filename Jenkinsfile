pipeline {
  agent any
  stages {
    stage('clone the') {
      steps {
        git(branch: 'main', url: 'https://github.com/learnaws288/springboot-app-b17.git')
      }
    }

    stage('build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('test') {
      steps {
        sh 'mvn test'
      }
    }

  }
}