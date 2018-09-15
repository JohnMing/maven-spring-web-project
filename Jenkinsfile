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
				def backup = '/home/webapps_backup/CounterWebApp_'+currentBuild.number+'.war'
				def dest = '/home/webapps/CounterWebApp.war'
				def src = '/var/jenkins_home/workspace/SpringMVCWebDemo-pine/target/CounterWebApp.war'
				echo 'mv -f ${dest} ${backup}'
				echo 'cp -f ${dest} ${backup}'

			}
	  }
	}
	}
}
