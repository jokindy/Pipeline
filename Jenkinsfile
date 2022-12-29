pipeline {
    agent any
    stages {
        stage ('Git') {
         steps{
            echo "Git step in process"
             git branch: 'main', url: 'https://github.com/jokindy/TomcatTestApp.git'
             echo "Git step is finished"
          }
      }
      stage ('Deploy') {
                  steps {
                       script {
                         deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://192.168.216.78:8080/')], contextPath: '/PipelineJob', onFailure: false, war: 'webapp/target/*.war'
                     }
                   }
                }
    }
}
