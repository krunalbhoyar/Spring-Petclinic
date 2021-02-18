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
    }   #above part is running well , below part has issue
         
      stage('Quality Gate Status Check') {
          steps { 
              script{
          withSonarQubeEnv('sonarqube')
          sh 'mvn sonar:sonar'
                    }
          timeout(time: 1, unit: 'HOURS') {
          def qg = waitforQualityGate()
              if (qg.status != 'OK')
               error "Pipeline aborted due to quality gate failure: $(qg.status)"
              }
          }   
             sh 'mvn clean install'
          }
      }
}
