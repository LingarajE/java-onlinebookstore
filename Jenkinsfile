pipeline {
    agent {label "dev"}

    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/LingarajE/java-onlinebookstore.git'
            }
        }
        stage('Build the project') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Tomcat deployment') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'TomcatadminID', path: '', url: 'http://18.213.245.60:8080/')], contextPath: null, war: '**/*.war'
            }
        }        
    }
}
