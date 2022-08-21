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
                deploy adapters: [tomcat9(path: '', url: 'http://43.204.217.61:8080/')], contextPath: 'sample', onFailure: false, war: '**/*.war'
            }            
        }
    }
}
