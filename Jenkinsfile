pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean package'
            }
            post{
                success {
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deployto tomcat server') {
            steps{
                deploy adapters: [tomcat9(credentialsId: 'b4410129-0d61-438c-a6eb-1ba62f1ec3be', path: '', url: 'http://15.206.173.118:8090/')], contextPath: 'sample', war: '**/*.war'
            }            
        }
    }
}
