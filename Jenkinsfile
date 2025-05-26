pipeline {

    agent any

    stages {

        stage("Build"){
            steps {
                sh "./mvnw install"
            }
        }
        
        stage("run unit-test"){
            steps {
               sh "./mvnw test"
           }
       }
        stage("CodeScanning"){
            environment {
               SONAR_HOME = tool 'sonar-scan'
            }
            steps {
                withSonarQubeEnv('SonarServer') {
              
                    sh '''${SONAR_HOME}/bin/sonar-scanner \
                    -Dsonar.projectKey=myPETC \
                    -Dsonar.projectName=mypetclinc \
                    -Dsonar.sources=. \
                    -Dsonar.java.binaries=target/classes \
                    -Dsonar.exclusions=src/test/java/****/*.java \
                    -Dsonar.analysis.mode=publish \
                    -Dsonar.projectVersion=${BUILD_NUMBER}-${GIT_COMMIT_SHORT}
                    '''
                }
            }
        
        }
        stage('Quality Gate') {
            steps {
                timeout(time: 5, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
        
            }
        }
    }
}                   
    

        
    

