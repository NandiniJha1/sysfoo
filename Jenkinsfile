pipeline {
  agent any
  tools {
    maven 'Maven 3.6.3'
  }
  stages{
      stage("build"){
          steps{
              echo 'Compiling the code for sysfoo app'
              sh 'mvn compile'
          }
      }
      stage("Test"){
          steps{
              echo 'Clean test with unit test for sysfoo'
              sh 'mvn clean test'
          }
      }
      stage("Package"){
          steps{
              echo 'Generating artifacts for deployment'
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
