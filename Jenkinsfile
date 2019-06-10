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
                    bat 'mvn clean install '
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
			withSonarQubeEnv(sonarqube-7.5) {
bat 'mvn package -DskipTests -U sonar:sonar -Dsonar.branch.name=master -Dsonar.host.url=SONARQUBE_SERVER_URL -Dsonar.github.repository=https://github.com/sivapavanias/mavenex.git/ -Dsonar.github.login=sivapavanias -Dsonar.github.oauth=e7391e79fc16ddc16ba31cbf8e4835e1fcfeb0a3 -Dsonar.host.url=http://localhost:9000 -Dsonar.login=admin -Dsonar.password=admin -Dsonar.sources=. -Dsonar.projectBaseDir=C://Program Files (x86)//Jenkins//workspace//june-6th-2k19//src//main -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true'
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

