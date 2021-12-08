pipeline {
	agent any
	 environment {
 		 SONARQUBE_URL="http://79.137.37.35"
 		 SONARQUBE_PORT="9000"
                 SNARQUBE_LOGIN="cb109055acc601bfe954274edfeeaa71359ed058"
                 SNARQUBE_KEY="my_TP_project" 
	 }
	stages {
	stage('Clone') {
	steps {
		git 'https://github.com/silogwire/Rep_Test.git'
	}
	}
//	stage('Build') {
//		sh label: '', script: 'mvn clean compile'
//	emailext body: 'Your code was failed due to sonarqube quality gate', subject: 'Jenkins Failed Report', to: 'sihamlachir@gmail.com'

//	}
//        stage('Code verification') {
 //               sh label: '', script: 'mvn clean verify  sonar:sonar -Dsonar.projectKey=my_TP_project -Dsonar.host.url=http://79.137.37.35:9000 -Dsonar.login=cb109055acc601bfe954274edfeeaa71359ed058'
   //     }

	stage('Sonarqube') {
    steps {
     withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'ID_Secret') {

						sh 'mvn clean package sonar:sonar -Dsonar.login=d59c079a8ee100c3f1f14e92db651f9308ab9fd3'
       
 }
}
}
	    stage("Quality Gate"){
	steps {
        timeout(time: 15, unit: 'MINUTES') { // Just in case something goes wrong, pipeline will be killed after a timeout
        def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
            if (qg.status != 'OK') {
                error "Pipeline aborted due to quality gate failure: ${qg.status}"
            }
        }
    }}
}
}
