pipeline{
    agent {
		docker {
			image 'qaninja/rubywd'
		}
	}
    
    stages{
        
        stage('Build'){
          steps {  
              echo 'Building or Resolv Dependencies'
			  sh 'rm -f Gemfile.lock'
			  sh 'bundle install'
            }
        }
        
        stage ('Test'){
            steps{
                echo 'Running regression tests'
				sh 'bundle exec cucumber -p ci'
            }
        }
        
        stage ('UAT'){
            steps{
                echo 'Wait for User Acceptance'
                input(message: 'Go to production?', ok:'Yes')
            }
        }
        
        stage('Prod'){
            steps{
                echo 'Webapp is ready :)'
            }
        }
    }
}