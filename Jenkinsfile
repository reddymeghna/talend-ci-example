pipeline {
  agent any
  environment {
    JAVA_HOME = "C:\\Program Files\\Java\\jdk-21"
    TALEND_CLI = "C:\\Program Files (x86)\\Talend-Studio\\studio\\Talend-Studio-win-x86_64"
    JOB_NAME = "CustomerLoggerJob"
  }
  parameters {
    string(name: 'CSV_FILE_PATH', defaultValue: 'D:/Downloads/customers.csv')
  }
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main',
            url: 'https://github.com/reddymeghna/talend-ci-example.git'
      }
    }
    stage('Unzip Job') {
      steps {
        bat 'powershell -Command "Expand-Archive -Force CustomerLoggerJob.zip .\\job2"'
      }
    }
    stage('Run Talend Job') {
      steps {
        bat '''
        cd job2\\CustomerLoggerJob
        call CustomerLoggerJob_run.bat --context=Default ^
        --context_param CSV_FILE_PATH=%CSV_FILE_PATH%
        '''
      }
    }
  }
}
