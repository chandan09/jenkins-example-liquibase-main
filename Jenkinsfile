pipeline {
  agent any
/*  environment {
  MYSQL_CRED = "mysql_id"
}*/
  stages {
    stage('Test') {
      steps {
        bat 'liquibase -version'
      }
    }
    stage('Status') {
      steps {
//        bat 'liquibase status --url="jdbc:mysql://localhost:3306/inventory" --changeLogFile=my_app-wrapper.xml --username=$MYSQL_CRED_USR --password=$MYSQL_CRED_PSW'
          bat' liquibase status --url="jdbc:mysql://localhost:3306/inventory" --changeLogFile=my_app-wrapper.xml --username="testuser" --password="password"'
      }
    }
    stage('Update') {
      steps {
//        bat 'liquibase update --url="jdbc:mysql://localhost:3306/inventory" --changeLogFile=my_app-wrapper.xml --username=$MYSQL_CRED_USR --password=$MYSQL_CRED_PSW'
        bat 'liquibase update --url="jdbc:mysql://localhost:3306/inventory" --changeLogFile=my_app-wrapper.xml --username="testuser" --password="password"'
      }
    }
  }
  post {
    always {
      cleanWs()
    }
  }
}
