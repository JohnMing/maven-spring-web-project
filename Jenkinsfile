pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('mvn') {
      steps {
        sh 'mvn -B -DskipTests clean package'
        sh 'echo pwd'
        sh 'cp /var/jenkins_home/workspace/SpringMVCWebDemo-pine/target/CounterWebApp.war /home/johnming/webapp/CounterWebApp.war'
      }
    }
  }
}
