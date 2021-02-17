pipeline {

    agent any
    
     stages {
      stage ('Source composition analysis') {
        steps {
          sh 'rm owasp* || true'
          sh 'wget "https://raw.githubusercontent.com/krunalbhoyar/Spring-Petclinic/master/owasp-dependency-check.sh" '
          sh 'chmod +x owasp-dependency-check.sh'
          sh 'sudo chmod 777 odc-reports/'
          sh 'bash owasp-dependency-check.sh'
          sh 'cat /var/lib/jenkins/workspace/Assignment_2/odc-reports/dependency-check-report.xml'
            
          
        }
    }   
         
      stage('SAST') {
          steps { 
          withSonarQubeEnv('sonarqube')
              sh 'mvn sonar:sonar'
              sh 'cat target/sonar/report-task.txt'
          }
      }
}
}
