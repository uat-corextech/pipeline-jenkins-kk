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
        stage('build stage') {
            steps {
                // if i am putting this jenkinsfile in the same project repo,
                // it will automatically checkout this repo new revision.
               // git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
                sh 'mvn clean package -DskipTests=true'
                archiveArtifacts '/home/tushar/agent1/workspace/pipeline-jenkins-kk_main/target/spring-petclinic-*.jar'
            }
        }

        stage('unit test') {
            steps {
                sh 'mvn test'
                junit(testResults: '/home/tushar/agent1/workspace/pipeline-jenkins-kk_main/target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
            }
        }
    }
}
 //