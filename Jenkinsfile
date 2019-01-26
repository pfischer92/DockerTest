pipeline{
    agent any
    tools {
        maven 'mvn3.6'
    }
    stages{
        stage('Checkout'){
            steps {
                checkout scm
                    sh 'mvn clean'
            }
        }
        stage('Build'){
            steps {
                sh 'mvn package'
            }
        }
        stage('Deploy'){
            steps {
                sh 'mkdir -p /var/jenkins_home/download'
                sh 'cp ./target/*.jar /var/jenkins_home/download'
            }
        }
    }
    post {
        always {
            // Publish test results
            junit 'target/surefire-reports/*.xml'
        }
    }
}
