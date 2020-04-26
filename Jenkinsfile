#!/bin/groovy
pipeline {
  agent any
 
  tools {nodejs "node"}

  stages {
    stage('Startup') {
      steps {
        script {
          sh 'npm i'
        }
      }
    }
    stage('Test') {
      steps {
        script {
          sh 'npm run test'
        }
      }
      post {
        always {
          step([$class: 'CoberturaPublisher', coberturaReportFile: 'output/coverage/jest/cobertura-coverage.xml'])
        }
      }
    }
  }
}