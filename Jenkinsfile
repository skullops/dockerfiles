stage('build and push') {
  ansiblePlaybook colorized: true, credentialsId: '36a62388-6f9b-4e41-9dbd-6083dc8019d6', installation: 'ansible 2.2.1.0', limit: 'localhost', playbook: '${WORKSPACE}/playbook.yml', sudoUser: null
}
