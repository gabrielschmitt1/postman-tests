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
            }
      }
      stage('Test') {
        steps {
            echo 'Running regression tests'
            sh 'newman run TestedaApi_reqres.postman_collection.json --reporters cli,junit --reporter-junit-export report.xml'
        }
      }
      stage('Prod') {
         steps {
            echo 'System is ready'
         }
      }
   }
}
