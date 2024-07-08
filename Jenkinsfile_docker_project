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
    stage('Build Docker OWN image') {
            steps {
                sh "sudo docker build -t learndevops16/javaappb50:${BUILD_ID} ."

            }
           
        }
    stage('docker push ') {
     steps {
     withCredentials([string(credentialsId: 'DOCKER_HUB_PWD', variable: 'DOCKER_HUB_PASS_CODE')])  {
    // some block
    sh "sudo docker login -u learndevops16 -p $DOCKER_HUB_PASS_CODE"
}
 sh "sudo docker push learndevops16/javaappb50:${BUILD_ID}"

}
} 
stage('Deploy to Dev Env') {
steps {
sshagent(['DEV_ENV']) {
    sh "ssh -o StrictHostKeyChecking=no ubuntu@3.110.31.234  sudo docker rm -f app1" 
  sh "ssh -o StrictHostKeyChecking=no ubuntu@3.110.31.234  sudo docker run -itd --name app1 -p 8080:8080 learndevops16/javaappb50:${BUILD_ID}" 
}
}
}

  }
}
