pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
                echo 'Success'
            }
        }
      stage('Test'){
        steps('Test')
        {
          sh 'mvn test'
          echo 'Success'
          post{
            always{
              junit 'target/surefire-reports/*.xml'
            }
          }
        }
      }
      stage ('Deploy'){
        steps{
          sh 'mvn deploy'
          echo 'Deployment Successful'
        }
      }
    }
  post{
    failure{
      echo 'Pipeline failed'
    }
  }
}


