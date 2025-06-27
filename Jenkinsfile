pipeline {
    agent any
    stages {

        stage('pull') {
            steps {
                git branch: 'main', url: 'https://github.com/PraveenKuber/'
            }
        }
        stage('compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('build') {
            steps {
                 sh 'mvn clean install'
            }
        }

        
    }

  post {
  success {
    mail to: 'abc.test.team@gmail.com',
         subject: "SUCCESS: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
         body: "Good news! Build succeeded: ${env.BUILD_URL}"
  }
  failure {
    mail to: 'abc.test.team@gmail.com',
         subject: "FAILURE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
         body: "Unfortunately, build failed: ${env.BUILD_URL}"
  }
}
}
