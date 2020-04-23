pipeline {

    agent any
    
     
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
        stage('Building SONAR') {
            steps{
                try{     
sh './mvnw clean sonarqube'
}
        catch (e) {emailext attachLog: true, body: 'See attached log', subject: 'BUSINESS Build Failure', to: 'sakthisivani18@gmail.com'
step([$class: 'WsCleanup'])
return
}
        }
        
        stage ('sonar') {

            steps {


                    sh '/opt/apps/devops/sonar-scanner-4.2.0.1873-linux/bin/sonar-scanner'

            }

         }     
        
    }
}
}
