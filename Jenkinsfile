pipeline {

    agent any
    
    stage ('Source composition analysis') {
       steps {
          sh 'rm owasp* || true'
          sh 'wget "https://raw.githubusercontent.com/krunalbhoyar/Spring-Petclinic/master/owasp-dependency-check.sh" '
          sh 'chmod +x owasp-dependency-check.sh'
          sh 'bash owasp-dependency-check.sh'
          sh 'cat /var/lib/jenkins/OWASP-Dependency-Check/reports/dependency-check-report.xml'
        }
    }
}
