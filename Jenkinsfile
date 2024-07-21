pipeline {
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        git 'https://github.com/xoXen/JenkinsDependencyCheckTest.git'
      }
    }

    stage('OWASP Dependency-Check Vulnerabilities') {
      steps {
        dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'OWASP Dependency-Check', nvdCredentialsId: 'NVD-API-KEY'
      }
    }
  }  
  post {
    success {
      dependencyCheckPublisher pattern: 'dependency-check-report.xml'
    }
  }
}