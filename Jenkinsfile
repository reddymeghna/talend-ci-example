pipeline {
 agent any
 environment {
 JAVA_HOME = "C:\\Program Files\\Java\\jdk-21"
 TALEND_CLI = "C:\\Talend\\Talend-Studio-win-x86_64"
 JOB_NAME = "CI_CD_DEMO_PROJECT"
 }
 parameters {
 string(name: 'CSV_FILE_PATH', defaultValue: 
'C:/TalendStudio/customers.csv')
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
 bat 'powershell -Command "Expand-Archive -Force 
CI_CD_DEMO_PROJECT_0.1.zip .\\job2"'
 }
 }
 stage('Run Talend Job') {
 steps {
 bat '''
 cd job2\\CI_CD_DEMO_PROJECT
 call CI_CD_DEMO_PROJECT_run.bat --context=Default ^
 --context_param CSV_FILE_PATH=%CSV_FILE_PATH% ^
 '''
 }
 }
 }
}
