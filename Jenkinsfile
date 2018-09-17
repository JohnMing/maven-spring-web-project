pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }
  }
  
  stages {
	stage('mvn pack') {
	  steps {
		sh 'mvn -B -DskipTests clean package'
	  }
	}

	stage('backup') {
			steps {
			sh 'pwd'

			script{
				def backup = '/root/home/webapps_backup/CounterWebApp_'+currentBuild.number+'.war'
				def dest = '/root/home/webapps/CounterWebApp.war'
				def src = '/root/jenkins_home/jenkins-data/workspace/maven-spring-web-project/target/CounterWebApp.war'
				sh "mv  ${dest} ${backup}"
				sh "cp  ${src} ${dest}"

			}
	  }
	}
	}
}
