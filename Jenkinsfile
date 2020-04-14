pipeline {

  agent any
  environment {
    //adding a comment for the commit test
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.1.4'
    BG = "Deloitte"
    WORKER = ''
      }
  stages {
  stage('Build application'){
steps{
 bat 'mvn -B -U -e -V clean -DskipTests package'
}
}
     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Test'
        APP_NAME = 'Scheduler-test'
      }
      steps {
             bat 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
    
  }

  
}