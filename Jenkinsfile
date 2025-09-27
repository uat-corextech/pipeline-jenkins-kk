pipeline {
    agent any

    tools {
        // Uses Maven installation configured in Jenkins as "M398"
        maven "M398"
    }

    stages {
        stage('mvn version print') {
            steps {
                sh 'echo "print version"'
                sh 'mvn --version'
            }
        }
       stage('60-second loop') {
            steps {
                script {
                    for (int i = 1; i <= 60; i++) {
                        echo "Second: ${i}"
                        sleep time: 1, unit: 'SECONDS'
                    }
                }
            }
       }
        stage('build stage') {
            steps {
                // if i am putting this jenkinsfile in the same project repo,
                // it will automatically checkout this repo new revision.
               // git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
                sh 'mvn clean package -DskipTests=true'
            }
        }

        stage('unit test') {
            steps {
                sh 'mvn test'
            }
        }
    }
}
 //