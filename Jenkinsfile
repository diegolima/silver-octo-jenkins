pipeline {
  agent any
  stages {
    stage('swarm-1') {
      steps {
        echo 'Starting Swarm-1 Maintenance'        
      }
    }
    stage('Container Cleanup') {
      steps {
        echo 'Container Cleanup'
        sshagent(credentials: ['swarm-root']) {
          sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker container prune -f"
        }
      }
    }
    stage('Volume Cleanup') {
      steps {
        echo 'Volume Cleanup'
        sshagent(credentials: ['swarm-root']) {
          sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker volume prune -f"
        }
      }
    }
    stage('Image Cleanup') {
      steps {
        echo 'Image Cleanup'
        sshagent(credentials: ['swarm-root']) {
          sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker image prune -a -f"
        }
      }
    }
  }
  environment {
    swarm_login = 'root'
    swarm_port = '9022'
  }
}