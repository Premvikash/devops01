pipeline {
    agent {
    docker { image 'kaiwinter/docker-java8-maven' }
    }
    stages {
        stage('Preparation') {
            steps {
            git 'https://github.com/Premvikash/java-maven-ci.git'
            }
        }
        stage('Build') {
            steps {
            sh "mvn -Dmaven.test.failure.ignore clean package"
            }
        }
        /*stage('Sonar') {
            steps {
            sh "mvn -Dmaven.test.failure.ignore sonar:sonar '-Dsonar.host.url=http://localhost:9000' '-Dsonar.login=c0807f0eab3eae1d46f2e175f9dee913bed16698'"
            }
        }*/
        stage('Results') {
            steps {
            junit '**/target/surefire-reports/TEST-*.xml'
            archive 'target/*.jar'
            }
        }
    }
}