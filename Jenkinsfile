 pipeline { 
     agent any 
     tools { 
         maven 'maven'  // Ensure Maven is correctly configured in Global Tool Configuration 
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
