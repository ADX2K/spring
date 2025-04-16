pipeline {
  agent any
  tools {
    maven 'maven'
  }
  stages {
    stage ("Clean up") {
      steps {
        deleteDir()
      }
    }
    stage ("Clone repo") {
      steps {
        sh "git clone https://github.com/ADX2K/spring.git"
      }
    }
    stage ("Generate backend images") {
      steps {
        dir("spring") {
          sh "mvn clean install"
          sh "docker build -t docexp1-spring ."
        }
      }
    }
    stage ("Run Docker compose") {
      steps {
        dir("spring") {
          sh "docker-compose up -d"
        }
      }
    }
  }
}
