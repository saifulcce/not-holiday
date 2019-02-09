pipeline {
    agent { node { label 'appnode01' } }

    
    stages {
        
        stage('cleanup') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'development'){
                        sh 'if [ -d  /var/www/html/not-holiday-dev ]; then rm -fr  /var/www/html/not-holiday-dev; fi'

                    } else if (env.BRANCH_NAME == 'staging'){
                        sh 'if [ -d  /var/www/html/not-holiday-stage ]; then rm -fr  /var/www/html/not-holiday-stage; fi'

                    } else if (env.BRANCH_NAME == 'production'){
                         sh 'if [ -d  /var/www/html/not-holiday-prod ]; then rm -fr  /var/www/html/not-holiday-prod; fi'

                    } else {
                       echo "I dont build other branches"
                    }
                }
            }
        }
		
        stage('GetCode') {
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
		
		stage('StartService') {
            steps {
                script {
                    if (env.BRANCH_NAME == 'development'){
                        sh 'sudo service apache2 restart'

                    } else if (env.BRANCH_NAME == 'staging'){
                        sh 'sudo service apache2 restart'

                    } else if (env.BRANCH_NAME == 'production'){
                        sh 'sudo service apache2 restart'

                    } else {
                       echo "I dont build other branches"
                    }
                }
            }
        }




    }
}
