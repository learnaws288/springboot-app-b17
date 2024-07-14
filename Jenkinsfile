pipeline {
     agent { label 'java' } 

    stages {
        stage('git pull') {
            steps {
               git branch: 'main', url: 'https://github.com/learnaws288/springboot-app-b17.git'
            }
        }
        stage('package') {
            steps {
             sh 'mvn clean package'
            }
        }
    }
}
