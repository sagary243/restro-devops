node {
	stage('prepare') {
		git branch: 'main', poll: false, url: 'https://github.com/sagary243/restro-devops.git'
	}
	
	stage('build') {
		def mvnHome = tool 'MAVEN'
		withEnv(["MVN_HOME=$mvnHome"]){
			sh '"$MVN_HOME/bin/mvn" clean compile package'
		}
	}
	
	stage('deploy') {
		deploy adapters: [tomcat9(credentialsId: 'tomcatdeploy', path: '', url: 'http://3.111.213.158:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
	}

}
