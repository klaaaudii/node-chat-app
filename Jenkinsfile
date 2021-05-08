pipeline {
    agent any
	tools{nodejs "NodeJS"}
    stages {
	stage('Build') { 
            steps {
                echo 'Building..'
                sh 'npm nstall'
            }
	    post {
		success {
		    emailext attachLog: true,
		        body: "${currentBuild.currentResult} in job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
		        recipientProviders: [developers(), requestor()],
		        to: 'klaaudia.baran@gmail.com',
		        subject: "JENKINS successful build"
		}
		failure {
		    emailext attachLog: true,
		        body: "${currentBuild.currentResult} in job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
		        recipientProviders: [developers(), requestor()],
		        to: 'klaaudia.baran@gmail.com',
		        subject: "JENKINS build failed"
		}
        
    }
}
		
        
        stage('Test') {
            steps {
                echo 'Testing..'
		sh 'npm run test'
            }
	   post {
		success {
		    emailext attachLog: true,
		        body: "${currentBuild.currentResult} in job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
		        recipientProviders: [developers(), requestor()],
		        to: 'klaaudia.baran@gmail.com',
		        subject: "JENKINS successful test"
		}
		failure {
		    emailext attachLog: true,
		        body: "${currentBuild.currentResult} in job ${env.JOB_NAME} build ${env.BUILD_NUMBER}",
		        recipientProviders: [developers(), requestor()],
		        to: 'klaaudia.baran@gmail.com',
		        subject: "JENKINS test failed"
		}
		
	    }
	}
     }        
 }
    
    
