pipeline {
 
    agent { node { label 'hosting' } }

    stages {
                                     
        stage('cleanup docker system') {

            steps {

                dir('.build-automation/docker-image-management') {

                    sh 'bash ./cleanup-local-docker-system.bash'
                    
                }                

            }

        }   

        stage('deploy container') {

            steps {

                dir('.build-automation/local-execution-management') {

                    sh 'bash ./deploy-latest-docker-image-localhost.bash'

                }                

            }

        }

        stage('cleanup docker again') {

            steps {

                dir('.build-automation/docker-image-management') {

                    sh 'bash ./cleanup-local-docker-system.bash'

                }                 

            }

        }

        stage('monitor deployments') {

            steps {

                dir('.build-automation/local-execution-management') {

                    sh 'bash ./display-container-usage.bash'

                }                

            }

        }
              
}}