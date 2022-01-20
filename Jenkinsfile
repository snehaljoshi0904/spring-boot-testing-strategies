node{

stage('Checkout')  {
	
 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gittest', url: 'https://github.com/snehaljoshi0904/spring-boot-testing-strategies.git']]])
  }

stage('Initial Setup'){

sh "mvn clean compile"
}
	

}
