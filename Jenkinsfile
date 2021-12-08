pipeline {
  agent any
  environment {
  MYSQL_CRED = "mysql_id"
}
  stages {
    stage('Status') {
      steps {
        sh 'liquibase status --url="jdbc:mysql://localhost:3306/chandandb" --changeLogFile=my_app-wrapper.xml --username=$MYSQL_CRED_USR --password=$MYSQL_CRED_PSW'
      }
    }
    stage('Update') {
      steps {
        sh 'liquibase update --url="jdbc:mysql://localhost:3306/chandandb" --changeLogFile=my_app-wrapper.xml --username=$MYSQL_CRED_USR --password=$MYSQL_CRED_PSW'
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
