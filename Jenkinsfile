pipeline {
    agent any

    tools {
        maven 'Maven' // Use the configured Maven in Jenkins
    }

    environment {
        MAVEN_HOME = "C:\\Program Files\\Apache\\maven"
        PATH = "${MAVEN_HOME}\\bin;${env.PATH}"
    }

    stages {
        stage('Build') {
            steps {
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
