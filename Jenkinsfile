pipeline {
   agent {
       docker {
           image 'postman/newman_alpine33'
       }
   }

   stages {
      stage('Build') {
         steps {
            echo 'Building or resolve dependences'
            sh 'newman --version'
            sh 'npm install -g newman-reporter-html'
            }
      }
      stage('Test') {
        steps {
            echo 'Running regression tests'
            sh 'newman run TestedaApi_reqres.postman_collection.json --reporters cli,html --reporter-html-export teste.html'
        }
      }
      stage('Prod') {
         steps {
            echo 'System is ready'
         }
      }
   }
}
