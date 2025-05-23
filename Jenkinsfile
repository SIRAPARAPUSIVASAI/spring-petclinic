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
    }
}
        
    

