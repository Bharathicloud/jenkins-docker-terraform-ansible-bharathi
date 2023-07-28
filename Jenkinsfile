pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        script{
                def mvnHome = tool name: 'maven', type: 'maven'
                sh "${mvnHome}/bin/mvn package"
        }
      }
    }
    stage('Building Docker Image') {
      steps{
        script {
          sh "docker build -t bharathid/cicd-poc-jenkins-bharati:$BUILD_NUMBER ."
        }
      }
    }
    stage('Push Image To Docker Hub') {
      steps{
        script {
          sh "echo $USER"
          sh "docker login -u bharathid -p Amazon@2312"
          sh "docker push bharathid/cicd-poc-jenkins-bharati:$BUILD_NUMBER"
          }
        }
      }
    }
}

