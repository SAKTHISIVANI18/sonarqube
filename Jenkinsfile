pipeline {

    agent {
    label 'testagent'
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
        stage ('test') {
            steps{
                testcompletetest generateMHT: true,
                    launchType: 'lckdt',
                    project" 'sonarqube',
                    suite: 'Projects\\JenkinsTests.pjs',
                        test: 'MyKDT',
                        useTCService: true,
                        userName: 'SAKTHISIVANI18',
                userPassword: 'Supsara1831'
            }
        }
                
        
        stage ('sonar') {

            steps {


                    sh '/opt/apps/devops/sonar-scanner-4.2.0.1873-linux/bin/sonar-scanner'

            }

         }     
        
    }
}
