pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven 'Maven3.8.6'
    }

    stages {
        stage ('Build') {
            steps {
                echo "Build in process"
                sh 'mvn clean install'
                echo "Build is finished"
            }
        }
        stage ('Deploy') {
            steps {
                 script {
                   deploy adapters: [tomcat8(credentialsId: '7aaf9731-98ce-4f27-aaf7-6f289bd37ad5', path: '', url: 'http://192.168.216.78:8080')], contextPath: '/TomcatMavenApp', onFailure: false, war: 'target/*.war'
               }
             }
          }

    }
}

