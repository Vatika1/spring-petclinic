pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './mvnw package'
        echo 'Building'
        emailext(subject: 'Starting', body: '''<p>Job is starting:</p>
            <p><a href=\'http://localhost:9090/job/spring-petclinic/job\'></a></p>''', to: 'vatikaprasad@gmail.com', recipientProviders: [[$class: 'CulpritsRecipientProvider'],[$class: 'RequesterRecipientProvider']])
      }
    }

    stage('Test') {
      steps {
        echo 'Testing'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying'
      }
    }

  }
  post {
    success {
      emailext(subject: 'Success: Job is built successfully', body: '''<p>Success:</p>
            <p>Check console output at &QUOT;<a href=\'http://localhost:9090/job/spring-petclinic/job\'></a>&QUOT;</p>''', to: 'emailext(subject: 'Starting', body: '''<p>Job is starting:</p>
            <p><a href=\'http://localhost:9090/job/spring-petclinic/job\'></a></p>''', to: 'vatikaprasad@gmail.com', recipientProviders: [[$class: 'CulpritsRecipientProvider'],[$class: 'RequesterRecipientProvider']])', recipientProviders: [[$class: 'CulpritsRecipientProvider'],[$class: 'RequesterRecipientProvider']])
    }

    failure {
      emailext(subject: 'Failed', body: '''<p>Job failed:</p>
            <p><a href=\'http://localhost:9090/job/spring-petclinic/job\'></a></p>''', to: 'vatikaprasad@gmail.com', recipientProviders: [[$class: 'CulpritsRecipientProvider'],[$class: 'RequesterRecipientProvider']])
    }

  }
}
