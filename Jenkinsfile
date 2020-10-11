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
   stage('Deploy') {
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws_user', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
			ansiblePlaybook becomeUser: null, credentialsId: 'ssh_user', disableHostKeyChecking: true, installation: 'ansible_install_dir', playbook: 'deploy.yaml', sudoUser: null
		}         
   }   
}
