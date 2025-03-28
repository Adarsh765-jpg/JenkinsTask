pipeline {
    agent any

    environment {
        JAVA_HOME = "C:\\Program Files\\Java\\jdk-21"
        PATH = "${JAVA_HOME}\\bin;${env.PATH}"
    }

    stages {
        stage('Build') {
            steps {
                bat 'java -version'
                bat 'mvn clean package'
            }
        }
        stage('Run JAR') {
            steps {
                bat 'java -jar target/simple-java-project-1.0-SNAPSHOT.jar'
            }
        }
    }
}
