pipeline {

    agent any

    stages {

        stage("Build"){
            steps {
                sh "./mvnw install"
            }
        }
    }
}
stage("Run Unit-Tests"){
       steps {
        sh "./mvnw test"
    }
}
