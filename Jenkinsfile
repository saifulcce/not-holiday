pipeline {
    agent { node { label 'appnode01' } }

    
    stages {
        
        stage('Cleanup') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'development'){
                        sh 'git clone -b development git@github.com:saifulcce/not-holiday.git /var/www/html/not-holiday-dev '

                    } else if (env.BRANCH_NAME == 'staging'){
                        sh 'git clone -b staging git@github.com:saifulcce/not-holiday.git /var/www/html/not-holiday-stage '

                    } else if (env.BRANCH_NAME == 'production'){
                        sh 'git clone -b production git@github.com:saifulcce/not-holiday.git /var/www/html/not-holiday-prod '

                    } else {
                       echo "I dont build other branches"
                    }
                }
            }
        }




    }
}

