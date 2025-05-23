pipeline {

    agent any

    stages {

        stage("Build"){
            steps {
                sh "./mvnw install"
            }
        }
        
        //stage("run unit-test"){
            //steps {
               // sh "./mvnw test"
           // }
       // }
         stage("CodeScanning"){
            environment {
               SONAR_HOME = tool name: 'sonar-scan'
            }
            steps {
                withSonarQubeEnv('SonarServer') {
              
                    sh "${SONAR_HOME}/bin/sonar-scanner"
                }
            }

        }


    }
}
        
    

