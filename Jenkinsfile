pipeline {
  agent any
  stages {
    stage('swarm-1') {
      steps {
        echo 'Starting Swarm-1 Maintenance'
        sshagent(credentials: ['swarm-root']) {
          sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker container prune -f"
        }
        
      }
    }
    stage('Container Cleanup') {
      steps {
        echo 'Container Cleanup'
      }
    }
  }
  environment {
    swarm_login = 'root'
    swarm_port = '9022'
  }
}