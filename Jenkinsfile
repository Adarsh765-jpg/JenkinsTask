pipeline {

    agent any

    tools{
        maven "maven"
    }

    stages {
        stage('Build'){
            steps{
                bat 'mvn clean package'
            }
        }
        stage('Test'){
            steps{
                bat 'mvn test'
            }
        }
        stage('Run JAR') { 
           steps { 
               script {
            if (fileExists('target/simple-java-project-1.0-SNAPSHOT.jar')) {
                def output = powershell(returnStdout: true, script: 'java -jar target/simple-java-project-1.0-SNAPSHOT.jar').trim()
                echo "Output from JAR: ${output}"
            } else {
                error "JAR file not found! Ensure the build process creates the JAR."
            }
        }
    }
}

        
    }
}
