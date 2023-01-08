pipeline {
    agent any
     tools {
        maven 'Maven' 
        }
    stages {
        stage("Test"){
            steps{
                // mvn test
                bat 'mvn test'
            }
            
        }
        stage("Build"){
            steps{
                bat "mvn package"
                
            }
            
        }
        stage("Deploy on Test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat8(credentialsId: 'credtomcat', path: '', url: 'http://54.159.195.182:8090')], contextPath: 'spring-boot-war-example', war: '**/*.war'
            }
          }
        }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
