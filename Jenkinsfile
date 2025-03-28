pipeline {
    agent any

    tools {
        maven "maven"
    }

    stages {
        stage('Check Maven') {
            steps {
                bat 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                script {
                    def result = bat(returnStatus: true, script: 'mvn clean package')
                    if (result != 0) {
                        error "Maven build failed!"
                    }
                }
            }
        }

        stage('List Target Directory') {
            steps {
                bat 'dir target'
            }
        }

        stage('Verify JAR') {
            steps {
                script {
                    def jarPath = 'target/simple-java-project-1.0-SNAPSHOT.jar'
                    if (!fileExists(jarPath)) {
                        error "JAR file not found! Build might have failed."
                    } else {
                        echo "JAR file found: ${jarPath}"
                    }
                }
            }
        }

        stage('Run JAR') { 
            steps { 
                script {
                    def jarPath = 'target/simple-java-project-1.0-SNAPSHOT.jar'
                    def output = bat(returnStdout: true, script: "java -jar ${jarPath}").trim()
                    echo "Output from JAR: ${output}"
                }
            }
        }
    }
}
