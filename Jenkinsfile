pipeline {
  agent none
  
  tools {
    maven 'Maven 3.9.6'
  }
  
  stages{
      stage("build"){
          agent {
              docker { image 'maven:3.9.6-eclipse-temurin-17-alpine' }
          }
          steps{
              echo 'compiling sysfoo app'
              sh 'mvn compile'
          }
      }
      stage("test"){
          agent {
              docker { image 'maven:3.9.6-eclipse-temurin-17-alpine' }
          }
          steps{
              echo 'running unit tests'
              sh 'mvn clean test'
          }
      }
      stage("package"){
          agent {
              docker { image 'maven:3.9.6-eclipse-temurin-17-alpine' }
          }
          steps{
              echo 'packaging the app'
              sh 'mvn package -DskipTests'
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}
