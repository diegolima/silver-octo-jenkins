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
          environment {
            swarm_address = 'swarm-1.diegolima.org'
          }
          steps {
            sh "ping -c1 $swarm_address"
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker container prune -f"
            }
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker volume prune -f"
            }
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker image prune -a -f"
            }
          }
        }
        stage('Swarm-2') {
          environment {
            swarm_address = 'swarm-2.diegolima.org'
          }
          steps {
            sh "ping -c1 $swarm_address"
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker container prune -f"
            }
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker volume prune -f"
            }
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker image prune -a -f"
            }
          }
        }
        stage('Swarm-3') {
          environment {
            swarm_address = 'swarm-3.diegolima.org'
          }
          steps {
            sh "ping -c1 $swarm_address"
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker container prune -f"
            }
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker volume prune -f"
            }
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port $swarm_address docker image prune -a -f"
            }
          }
        }
      }
    }
  }
}