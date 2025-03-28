pipeline {
    agent any

    tools {
        maven 'Maven'  // Ensure Maven is set in Jenkins
    }

    environment {
        JAVA_HOME = "C:\\Program Files\\Java\\jdk-21"  // Ensure correct JDK
        PATH = "${JAVA_HOME}\\bin;${env.PATH}"
    }

    stages {
        stage('Clean and Build') {
            steps {
                bat 'mvn clean package -X'  // Enable debug logs
            }
        }
        stage('Run JAR') {
            steps {
                bat 'java -jar target/simple-java-project-1.0-SNAPSHOT.jar'
            }
        }
    }
}
