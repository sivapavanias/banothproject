pipeline {
    agent any


   tools {
        maven 'maven_3_5_0'
    }

 environment {
        def mavenHome = tool name: 'maven_3_5_0', type: 'maven'
        def JAVA_HOME = tool name: 'jdk-1.8', type: 'jdk'
    }

   


    stages {

        stage ('Compile stage') {
            steps {
                withMaven(maven: 'Maven_3_6_0') {

                    bat 'mvn --version'
                    bat 'mvn compile'
                }
            }
        }

        stage ('Testing stage') {

            steps {
                withMaven(maven: 'Maven_3_6_0') {
                    bat 'mvn test'
                }
             }
         }

        stage ('Deployment stage') {

                steps {
                withMaven(maven: 'Maven_3_6_0') {
                    bat 'mvn deploy'
                }
             }
         }
    }
}
