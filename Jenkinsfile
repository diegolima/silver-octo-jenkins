pipeline {
  agent any
  stages {
    stage('Swarm Maintenance') {
      steps {
        parallel(
          'Swarm-1':{
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker container prune -f"
            }
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker volume prune -f"
            }
            sshagent(credentials: ['swarm-root']) {
              sh "ssh -o StrictHostKeyChecking=no -l $swarm_login -p $swarm_port swarm-1.diegolima.org docker image prune -a -f"
            }
          },
        )
      }
    }
  }
  environment {
    swarm_login = 'root'
    swarm_port = '9022'
  }
}