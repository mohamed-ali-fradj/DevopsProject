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

            stage('SONARQUBE') {
                 steps {
                     sh 'mvn sonar:sonar -Dsonar.login=admin -Dsonar.password=sonar -Dmaven.test.skip=true';
                 }
            }
            stage('JUnit / Mockito') {
                 steps {
                       sh 'mvn test'
                       junit '**/target/surefire-reports/TEST-*.xml'
                        }
                 }

            stage('Nexus deploy') {
                 steps {
                 sh 'mvn deploy -Dmaven.test.skip=true'
                        }
                 }

        }
}
