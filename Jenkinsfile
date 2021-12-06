node {
	stage('Clone') {
		git 'https://github.com/silogwire/Rep_Test.git'
	}
	stage('Build') {
		sh label: '', script: 'mvn clean compile'
	}
}
