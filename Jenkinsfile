pipeline {

    agent any

    tools {
        maven "maven"
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Run JAR') { 
            steps { 
                script {
                    def jarPath = 'target/simple-java-project-1.0-SNAPSHOT.jar'
                    if (fileExists(jarPath)) {
                        def output = sh(returnStdout: true, script: "java -jar ${jarPath}").trim()
                        echo "Output from JAR: ${output}"
                    } else {
                        error "JAR file not found! Ensure 'mvn clean package' is successful."
                    }
                }
            }
        }
    }
}
