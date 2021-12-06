node {
	stage('Clone') {
		git 'https://github.com/silogwire/Rep_Test.git'
	}
	stage('Build') {
		sh label: '', script: 'javac src/main/java/hello/HelloWorld.java'
	}
}
