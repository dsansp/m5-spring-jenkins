pipeline {
    agent any
    tools {
        maven "Maven"
        jdk "JDK17"
    }
    stages {


        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
        stage('Site') {
            steps {
                bat 'mvn site'
            }
        }
         }
                stage('Sonar'){
                    steps {
                        bat 'mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=dsansp_m5-spring-jenkins -Dsonar.login=259b3cfadd9d8f5c91339ec14d3cb78997defd16 -Dsonar.host.url=https://sonarcloud.io -Dsonar.organization=dsansp'
                    }




}
}
