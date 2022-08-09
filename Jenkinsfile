pipeline {
  agent any
  stages {
    stage('Build Application') {
      post {
        success {
          echo 'Now Archiving the Artifacts....'
          archiveArtifacts '**/*.war'
        }

      }
      steps {
        sh 'mvn -f pom.xml clean package'
      }
    }

    stage('Create Tomcat Docker Image') {
      parallel {
        stage('Create Tomcat Docker Image') {
          steps {
            sh 'pwd'
            sh "docker build . -t tomcatsamplewebapp:${env.BUILD_ID}"
          }
        }

        stage('Stage1') {
          steps {
            sh 'touch test'
          }
        }

        stage('Stage 2') {
          steps {
            echo 'Test'
          }
        }

        stage('Stage3') {
          steps {
            echo 'Test3'
          }
        }

      }
    }

  }
}
