pipeline {
   agent any

   stages {
      stage('pull code') {
         steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/${branch}']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '0b777f21-0224-4fcc-9057-9a5ccefa9a8e', url: 'https://github.com/cuijiyao01/web_demo.git']]])
         }
      }
      stage('build code') {
         steps {
            sh label: '', script: 'mvn clean package'
         }
      }
      stage('publish code') {
         steps {
            deploy adapters: [tomcat8(credentialsId: 'c980bb5c-a86c-4f7d-bb66-5fb32edc086b', path: '', url: 'http://localhost:8080')], contextPath: null, war: 'target/*.war'
         }
      }
   }
}
