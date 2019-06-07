pipeline {
    agent any


   tools {
        maven 'maven_3_5_0'
    }

 environment {
        def maven = tool name: 'maven_3_5_0', type: 'maven'
        def JAVA_HOME = tool name: 'jdk1.8.0_191', type: 'jdk'
    }

   


    stages {

        stage ('Compile stage') {
            steps {
                withMaven(maven: 'maven_3_5_0') {
      // bat "\"${mvnHome}\"\\bin\\mvn -B verify"
                    bat 'mvn --version'
                    bat 'mvn clean install'
                }
            }
        }

        stage ('Testing stage') {

            steps {
                withMaven(maven: 'maven_3_5_0') {
                    bat 'mvn test'
                }
             }
         }
stage ('Sonar Analysis') {

            steps {
			withSonarQubeEnv {
   /home/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonarqubescanner/bin/sonar-scanner -Dsonar.host.url=http://localhost:9000 -Dsonar.projectName=june-6th-2k19 -Dsonar.projectVersion=1.0 -Dsonar.projectKey=meanstack:app -Dsonar.sources=. -Dsonar.projectBaseDir=C:\Program Files (x86)\Jenkins\workspace\june-6th-2k19\src\main
}

                
             }
         }
        stage ('Deployment stage') {

                steps {
                withMaven(maven: 'maven_3_5_0') {
                    bat 'mvn deploy'
                }
             }
         }
    }
}
