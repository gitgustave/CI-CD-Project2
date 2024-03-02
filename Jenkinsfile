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
                sh "mvn clean"
            }
        }

        stage("Test Application"){
            steps{
                sh "mvn test"
            }
        }
    }
}
