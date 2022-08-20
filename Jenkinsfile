pipeline{
    agent any
    tools{
        maven 'local_maven'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean packege'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveartifacts Artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat9(path: '', url: 'http://13.127.209.194:8080/')], contextPath: null, war: '**/*.war'
            }            
        }
    }

}
