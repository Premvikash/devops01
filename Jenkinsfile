node {
   def mvnHome
   stage('Preparation') {
      git 'https://github.com/Premvikash/devops01.git'
      mvnHome = tool 'M3'
   }
   stage('Build') {
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Build') {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore sonar:sonar '-Dsonar.host.url=http://localhost:9000' '-Dsonar.login=c0807f0eab3eae1d46f2e175f9dee913bed16698'"
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
