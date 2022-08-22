pipeline {
    
    agent none
    tools {
        maven 'Maven'
    }
    stages {
        stage('Checkout') {
            agent {label 'master'}
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Halesh1807/test3.git']]])
            }
        }
        
        stage('build') {
            agent {label 'sl2'}
            steps {
                sh 'mvn clean install'
            }
        }
        
        stage('Deploy to tomcat server') {
            agent {label 'sl2'}
            steps {
                deploy adapters: [tomcat9(credentialsId: 'b4410129-0d61-438c-a6eb-1ba62f1ec3be', path: '', url: 'http://15.206.173.118:8090/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
