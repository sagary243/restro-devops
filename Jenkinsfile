node {
	stage('prepare') {
		git branch: 'main', poll: false, url: 'https://github.com/sagary243/restro.git'
	}
	
	stage('build') {
		def mvnHome = tool 'MAVEN'
		withEnv(["MVN_HOME=$mvnHome"]){
			sh '"$MVN_HOME/bin/mvn" clean compile package'
		}
	}
	
	stage('deploy') {
		deploy adapters: [tomcat9(credentialsId: '42b14be3-65c1-4974-a66f-09bef07a51b8', path: '', url: 'http://43.204.148.145:8080/')], contextPath: null, war: '**/*.war'
	}

}
