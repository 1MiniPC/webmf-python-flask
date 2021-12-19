pipeline {
  agent { docker { image 'qnib/pytest' } }
  stages {
    stage('build') {
      steps {
        sh '''
            virtualenv venv --distribute
            . venv/bin/activate 
            pip install -r requirements.txt
            '''
      }
    }
    stage('test') {
      steps {
        sh 'python test.py'
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}