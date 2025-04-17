pipeline {
  agent any

  environment {
    IMAGE_NAME = 'nabeel/devops-app'
    TAG = 'latest'
  }

  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/khannabil2819/devops-cicd-project.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          dockerImage = docker.build("${IMAGE_NAME}:${TAG}")
        }
      }
    }

    stage('Push to DockerHub') {
      steps {
        script {
          docker.withRegistry('', 'khannabil') {
            dockerImage.push()
          }
        }
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        sh 'ansible-playbook ansible/deploy_k8s.yml'

        Fix: clone step using main branch
      }
    }
  }
}

