pipeline {
        agent any        
       // agent {
       // docker {
       //     image 'maven:3.9.3-eclipse-temurin-17'
       //     args '-v $HOME/.m2:/home/dirk/.m2'
       //         }
       // }
        environment {
                mvnHome = tool 'M3'
        }
    stages {
       // stage('Checkout') {
         //   steps {
                // Checkout Repository from GitHub
           //     git 'https://github.com/Pantao42/JenkinsPipelineTest.git'
            //}
        //}
        stage('Build') {
            steps {
                // Run Maven on a Unix agent.
                sh "${mvnHome}/bin/mvn -Dmaven.test.failure.ignore=true clean package"
                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
    }
        post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
        }
}
