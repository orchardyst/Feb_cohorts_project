pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                sh 'cd SampleWebApp mvn test'
            }
        }
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'ID_tomcatserver', path: '', url: 'http://18.118.252.194:8080')], contextPath: 'webapp', war: '**/*.war'
            }
        }
    }
}
