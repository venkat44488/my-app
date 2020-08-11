pipeline {
    agent any
    stages {
        stage('---clean---') {
            steps {
               // sh "mvn clean"
                echo " mvn clean step"
            }
        }
        stage('--test--') {
            steps {
              //  sh "mvn test"
                echo " mvn test step"
            }
        }
        stage('--package--') {
            steps {
               // sh "mvn package"
                echo "mvn package step"
            }
        }
    }
}
