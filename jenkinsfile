 node{
      stage('Clone') {
          checkout scm
      }
      stage('Ansible') {
          ansiblePlaybook (
            inventory: 'hosts.yml',
            playbook: 'playbook.yml',
            colorized: true,
        )
      }
}
