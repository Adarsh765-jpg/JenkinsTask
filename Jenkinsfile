pipeline {

    agent any

    tools {
        maven "maven"
    }

    stages {
        stage('Build') {
            steps {
                echo 'dir'
                echo 'pwd'
                bat 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Run JAR') { 
            steps { 
                script {
                    def jarPath = 'target/simple-java-project-1.0-SNAPSHOT.jar'
                    if (fileExists(jarPath)) {
                        def output = bat(returnStdout: true, script: "java -jar ${jarPath}").trim()
                        echo "Output from JAR: ${output}"
                    } else {
                        error "JAR file not found! Ensure 'mvn clean package' is successful."
                    }
                }
            }
        }
    }
}
