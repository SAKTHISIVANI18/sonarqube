pipeline {

    agent {
    label 'jacoco'
    }

     
    stages {
        
        stage ('checkout'){
            steps {
            git  'https://github.com/sshamit/jpetstore-6.git'
            }
        }

        

        stage ('package') {

            steps {


                    sh './mvnw clean package'

            }

         }
        stage ('coverage') {
            steps{
        jacoco buildOverBuild: true, changeBuildStatus: true, runAlways: true, skipCopyOfSrcFiles: true
            }
        }
        stage ('sonar') {

            steps {


                    sh '/opt/apps/devops/sonar-scanner-4.2.0.1873-linux/bin/sonar-scanner'

            }

         }     
        
    }
}
