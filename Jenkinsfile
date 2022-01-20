node{
    def MAVEN_HOME = tool "My_Maven"
    def JAVA_HOME = tool "JAVA_HOME"
    env.PATH = "${env.PATH}:${MAVEN_HOME}/bin"
    env.PATH = "${env.PATH}:${JAVA_HOME}/bin"
	
stage('Checkout')  {
	
 checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gittest', url: 'https://github.com/snehaljoshi0904/spring-boot-testing-strategies.git']]])
  }

stage('Initial Setup'){

sh "mvn clean compile"
}
stage('SonarQube analysis') {
		withSonarQubeEnv(installationName: 'sonar') {			 
                    bat 'C:\\apache-maven-3.6.0-bin\\apache-maven-3.6.0\\bin\\mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.0.1398:sonar -Dsonar.projectKey=spring-boot-testing-strategies -Dsonar.organization=learning-cicd'
    		}	 	
        }
	
stage("Quality Gate"){
  timeout(time: 1, unit: 'HOURS') { 
    def qg = waitForQualityGate() 
    if (qg.status != 'OK') {
      error "Pipeline aborted due to quality gate failure: ${qg.status}"
    }
}
}
