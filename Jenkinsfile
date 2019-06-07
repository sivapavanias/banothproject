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
       bat "\"${mvnHome}\"\\bin\\mvn -B verify"
                    //sh 'mvn --version'
                    //sh 'mvn clean install'
                }
            }
        }

        stage ('Testing stage') {

            steps {
                withMaven(maven: 'maven_3_5_0') {
                    //sh 'mvn test'
                }
             }
         }

        stage ('Deployment stage') {

                steps {
                withMaven(maven: 'maven_3_5_0') {
                    //bat 'mvn deploy'
                }
             }
         }
    }
}
