node{
	stage('SCM Checkout'){
		git branch: 'wartomcat', credentialsId: 'tomcat-dev', url: 'https://github.com/srjgrg/devopsprojects-1.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'maven-3.5.4', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deploy to Tomcat'){
		sshagent(['tomcatserver']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@http://3.15.238.149:/opt/tomcat9/webapps/'
	}
	}
}
