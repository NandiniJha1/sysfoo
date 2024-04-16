pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'Compiling the code for sysfoo app'
        sh 'mvn compile'
      }
    }

    stage('Test') {
      steps {
        echo 'Clean test with unit test for sysfoo'
        sh 'mvn clean test'
      }
    }

    stage('Package') {
      parallel {
          stage('Package') {
            when{ 
              branch 'master'
            }
            steps {
                echo 'Generating artifacts for deployment'
                sh 'mvn package -DskipTests'
              }
            
          }
          

        stage('TestA') {
          steps {
            sleep(time: 5, unit: 'SECONDS')
          }
        }

      }
    }

    stage('TestB') {
      steps {
        sleep 3
      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}
