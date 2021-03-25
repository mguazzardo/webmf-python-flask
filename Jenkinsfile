pipeline {
  agent { docker { image 'python:3.7.6' } }
  stages {
    stage('build') {
      steps {
        sh 'pip install -r requirements.txt'
      }
    }
    stage('test') {
      steps {
        sh '''
        python test.py
        curl localhost:5000
        '''
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}
