pipeline {
  agent {label "linux"}
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
    disableConcurrentBuilds()
  }
  stages {
    stage('Build') {
      steps {
        echo "Hello"
      }
    }
    stage('Test') {
      steps {
        echo "Testing the application"
      }
    }
    stage('Deploy Staging') {
      when {
        buildingTag()
      }
      steps {
        echo "Deploying tag to staging"
      }
    }
    stage('Deploy Prod') {
      when {
        beforeInput true
        buildingTag()
      }
      input {
        message "Okay to proceed?"
        submitter "nlscott83"
      }
      steps {
        echo "Deploying tag to production"
      }
    }
  }
}
