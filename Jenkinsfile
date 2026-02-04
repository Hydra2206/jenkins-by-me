pipeline {
  agent any
  stages {
    stage('Back-end') {
      agent {
        docker { image 'maven:3.8.1-adoptopenjdk-11' }
      }
      steps {
        sh 'mvn --version'
      }
    }
    stage('Checkout') {
            steps {
                git 'https://github.com/Hydra2206/jenkins-by-me.git'
                sh 'cd contentstack-java-news-web-app-example-master'
            }
    }
    stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
    }
    stage('Test') {
            steps {
                sh 'mvn test'
            }
    }
    stage('Package') {
            steps {
                sh 'mvn package -DskipTests'
            }
    }
    stage('Deploy') {
            steps {
                sh '''
                   echo "Deploying application..."
                   cp target/*.jar /opt/apps/myapp.jar
                   systemctl restart myapp
                '''
            }
        }
    }
  post {
    success {
        echo 'Pipeline completed successfully!'
    }
    failure {
        echo 'Pipeline failed!'
    }
  }
}