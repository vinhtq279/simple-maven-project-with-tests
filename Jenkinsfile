node ('master'){
  checkout scm
  stage ('Build'){
    withMave (maven: 'M3'){
      if (isUnix()){
        sh 'mvn -Dmave.test.failure.ignore clean package' 
      }
      else {
        bat 'mvn -Dmaven.test.failure.ignore clean package' 
      }
    }
  }
  stage('Results'){
    junit '**/target/surefire-reports/TEST-*.xml'
    archive 'target/*.jar'
  }
}
