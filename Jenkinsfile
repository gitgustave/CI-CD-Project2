pipeline {
    agent any
    options{
        //This is required if you want to clean before build
        skipDefaultCheckout(true)
    }
    tools {
        jdk 'java'
        maven 'maven_home'
    }

        environment {
        SCANNER_HOME = tool 'sonar-scanner'
        APP_NAME = "java-registration-app"
        RELEASE = "1.0.0"
        DOCKER_USER = "gustavepablo4"
        DOCKER_PASS = 'Docker-cred'
        IMAGE_NAME = "${DOCKER_USER}" + "/" + "${APP_NAME}"
        IMAGE_TAG = "${RELEASE}-${BUILD_NUMBER}"
	
    }
    stages{
        //stage("Clean Up WorkSpace"){
          //  steps {
            //    cleanWs()
            //}
        //}

        stage("Checkout from SCM"){
            steps{
                git branch: 'main', credentialsId: 'gitgustave', url: 'https://github.com/gitgustave/CI-CD-Project2'
            }
        }

        stage("Build Application "){
            steps{
                dir('project2') { 
                sh "mvn clean"
                }
            }
        }

        stage("Test Application"){
            steps{
                dir('project2'){ 
                sh "mvn test"
                }
            }
        }

        stage ('SonarQube Analysis') {
            steps {
              withSonarQubeEnv('SonarQube-Server') {
                dir('project2'){
                sh 'mvn -U clean install sonar:sonar'
                }
              }  

    }
}
}
}

