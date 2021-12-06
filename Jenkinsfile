node {
	stage('Clone') {
		git 'git@github.com:silogwire/Rep_Test.git'
	}
	stage('Build') {
		sh label: '', script: 'javac src/main/java/hello/HelloWorld.java '
	}
	stage('Run') {
		sh label: '', script: 'java src/main/java/hello/HelloWorld'
	}
}
