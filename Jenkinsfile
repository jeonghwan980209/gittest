pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/dong597/gittest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t dododong478/keduitlab:red .
        sudo docker push dododong478/keduitlab:red
        '''
      }
    }
    stage('deploy and service') {
      steps {
        sh '''
        sudo ansible-playbook to_node.yml
        sudo ansible-playbook to_master.yml
        '''
      }
    }
  }
}
