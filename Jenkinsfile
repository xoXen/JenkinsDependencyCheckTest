pipeline {
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        git 'https://github.com/xoXen/JenkinsDependencyCheckTest.git'
      }
    }

    stage('OWASP DependencyCheck') {
      steps {
        dependencyCheck additionalArguments: '--nvdApiDelay 8000 --format HTML --format XML', odcInstallation: 'OWASP Dependency-Check Vulnerabilities', nvdCredentialsId: 'NVD-API-KEY'
      }
    }
  }  
  post {
    success {
      dependencyCheckPublisher pattern: 'dependency-check-report.xml'
    }
  }
}