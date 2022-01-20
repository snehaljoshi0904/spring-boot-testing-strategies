node{
    def MAVEN_HOME = tool "MY_Maven"
    def JAVA_HOME = tool "JAVA_HOME"
    env.PATH = "${env.PATH}:${MAVEN_HOME}/bin"
    env.PATH = "${env.PATH}:${JAVA_HOME}/bin"
	
stage('Checkout')  {
	
 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gittest', url: 'https://github.com/snehaljoshi0904/spring-boot-testing-strategies.git']]])
  }

stage('Initial Setup'){

sh "mvn clean compile"
}
	

}
