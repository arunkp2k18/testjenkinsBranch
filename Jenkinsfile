pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add build steps here
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add test steps here
            }
        }

        stage('Deploy to Production') {
            when {
                expression { env.BRANCH_NAME == 'production' }
            }
            steps {
                echo 'Deploying to production...'
                sh 'cp -r * /portal'
            }
        }

        stage('Deploy to Dev') {
            when {
                expression { env.BRANCH_NAME == 'dev' }
            }
            steps {
                echo 'Deploying to dev...'
				sh 'cp -r * /tmp/'
                // Add deployment steps for dev here
            }
        }
	    stage('Restart Service'){
		    when {
			    branch "production" 
		    }
		    steps{
			    echo 'Restart Service'
		    }
	    }
    }

    post {
        always {
            echo 'Cleaning up...'
            // Add any cleanup steps here
        }
    }
}
