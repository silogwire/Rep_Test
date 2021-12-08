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
	emailext body: 'Your code was failed due to sonarqube quality gate', subject: 'Jenkins Failed Report', to: 'sihamlachir@gmail.com'

	}
//        stage('Code verification') {
 //               sh label: '', script: 'mvn clean verify  sonar:sonar -Dsonar.projectKey=my_TP_project -Dsonar.host.url=http://79.137.37.35:9000 -Dsonar.login=cb109055acc601bfe954274edfeeaa71359ed058'
   //     }
        stage('Sonarqube') {
    environment {
        scannerHome = tool 'SonarQubeScanner'
    }
        withSonarQubeEnv('sonarqube') {
                sh label: '', script: 'mvn clean package sonar:sonar -Dsonar.projectKey=my_TP_project -Dsonar.host.url=http://79.137.37.35:9000 -Dsonar.login=cb109055acc601bfe954274edfeeaa71359ed058'

        }
//        timeout(time: 10, unit: 'MINUTES') {
//            waitForQualityGate abortPipeline: true
///        }
          }
stage("Quality Gate") {
    timeout(time: 100, unit: 'MINUTES') {
              def qg= waitForQualityGate()
            if (qg.status!= 'OK'){
                error " Pipeline interrompu en raison d'un échec de la porte de qualité : ${qg.status} "
           }
        }         
              echo 'Quality Gate Passed'

  }
}
