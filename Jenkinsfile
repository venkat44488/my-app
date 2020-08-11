pipeline {
    agent any
    stages {
        stage('---clean---') {
            steps {
                // sh "mvn clean"
                echo " This stage suppose to clean "
                echo " modifying clean package"
                sleep 100
            }
        }
        stage('--test--') {
            steps {
                //sh "mvn test"
                echo " suppose to have mv test stage"
            }
        }
        stage('--package--') {
            steps {
                echo " maven package stage"
                //sh "mvn package"
            }
        }
    }
}
