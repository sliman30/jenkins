pipeline {
  agent {label agent1}
  stages {
    stage('BUILD') {
      steps {
        sh '''mvn clean install


'''
      }
    }

    stage('Test') {
      steps {
        sh 'echo test'
      }
    }

    stage('POST BUILD') {
      steps {
        archiveArtifacts(artifacts: '*/*.war', onlyIfSuccessful: true)
      }
    }

    stage('DEPLOY') {
      steps {
        deploy adapters: [tomcat9(credentialsId: '25593935-165d-49ac-a307-78949337d4ef', path: '', url: 'http://172.17.0.2:8080/')], contextPath: '/spark', war: 'target/*.war'
      }
    }

  }
}
