node {
   stage('Prepare') {
      git 'https://github.com/riviewz/fleetman-position-tracker'
   }
   stage('Build') {
      sh 'mvn package'
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
