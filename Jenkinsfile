pipeline {
   agent {
       docker {
           image 'postman/newman_alpine33'
           args '--entrypoint=""'
       }
   }
   stages {
      stage('Build') {
         steps {
            echo 'Building or resolve dependences'
            sh 'newman --version'
            sh 'npm install -g newman-reporter-html'
            sh 'npm install -g newman-reporter-junitfull'
            sh 'npm install -g newman-reporter-htmlextra'
            }
      }
      stage('Test') {
        steps {
            echo 'Running regression tests'
            sh 'newman run TestedaApi_reqres.postman_collection.json --reporters cli,junit,htmlextra --reporter-junit-export "report.xml" --reporter-htmlextra-export "newman_result.html"'
            junit "*.xml"
        }
      }
      post {
        always {
            emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'
        }
      }
      stage('Prod') {
         steps {
            echo 'System is ready'
         }
      }
   }
}

