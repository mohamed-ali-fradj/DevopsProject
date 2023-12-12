pipeline {
        agent any

        stages {
            stage('Chekout GIT'){
                steps {
                    echo 'Pulling...'
                        git branch: 'master' ,
                        url : 'https://github.com/mohamed-ali-fradj/DevopsProject.git'
                }
            }

            stage('MVN CLEAN') {
                steps{
                    sh 'mvn clean install';

                }

            }

             stage('MVN COMPILE') {
                steps{
                    sh 'mvn compile';

                }

            }

        }
}
