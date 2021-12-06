node {
	 environment {
 		 SONARQUBE_URL="http://79.137.37.35"
 		 SONARQUBE_PORT="9000"
                 SNARQUBE_LOGIN="cb109055acc601bfe954274edfeeaa71359ed058"
                 SNARQUBE_KEY="my_TP_project" 
	 }

	stage('Clone') {
		git 'https://github.com/silogwire/Rep_Test.git'
	}
	stage('Build') {
		sh label: '', script: 'mvn clean compile'
	}
        stage('Code verification') {
                sh label: '', script: 'mvn clean verify  sonar:sonar -Dsonar.projectKey=$SNARQUBE_KEY -Dsonar.host.url=http://79.137.37.35:$SONARQUBE_PORT -Dsonar.login=$SNARQUBE_LOGIN'
        }

}
