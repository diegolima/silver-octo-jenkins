pipeline {
  agent any
  stages {
    stage('Swarm Maintenance') {
      environment {
        swarm_login = 'root'
        swarm_port = '9022'
      }
      parallel {
        stage('Swarm-1') {
          steps {
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker container prune -f"
            }
            
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker volume prune -f"
            }
            
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker image prune -a -f"
            }
            
          }
        }
        stage('Swarm-2') {
          steps {
            echo 'Swarm-2'
          }
        }
        stage('Swarm-3') {
          steps {
            echo 'Swarm-3'
          }
        }
      }
    }
  }
}