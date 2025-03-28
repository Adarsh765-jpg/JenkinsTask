 pipeline { 
     agent any 
     tools { 
         maven 'maven'  // Ensure Maven is correctly configured in Global Tool Configuration 
     } 

    environment {
         JAVA_HOME = "C:\\Program Files\\Java\\jdk-21"  // Ensure correct JDK
         PATH = "${JAVA_HOME}\\bin;${env.PATH}"
     }
  
     stages { 
         stage('Build') { 
             steps { 
                 bat 'mvn clean package -X' 
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
                     // Run the JAR file and capture the output 
                     def output = bat(script: 'java -jar target/simple-java-project-1.0-SNAPSHOT.jar', returnStdout: true).trim() 
  
                     // Print the output to Jenkins console 
                     echo "Output from JAR: ${output}" 
                 } 
             } 
         } 
     } 
 } 
