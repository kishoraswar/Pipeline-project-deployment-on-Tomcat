pipeline {  
   agent any

    stages {  
            stage ('Git-Checkout') {  
                steps{
                    git 'https://github.com/kishoraswar/Pipeline-project-deployment-on-Tomcat.git'
                    echo "Checkout successful";
                    sh "mvn --version"
                } 
            }
            stage ('Compile') {  
                  steps{
                    sh  "mvn compile"
                    echo "test successful";
                    
                } 
            }
            stage ('Build') {  
                  steps{
                    sh "mvn clean"
                    sh "mvn package"
                    echo "build successful";
                    
                } 
            }
             stage ('Test') {  
                  steps{
                    sh "mvn test"
                    echo "test successful";
                } 
            }
            
        stage ('Deploy') {
            steps{
            deploy adapters: [tomcat9(credentialsId: '7af3ce34-1f77-4e38-9ce1-bced34023add',path: '', url: 'http://localhost:8084/')], contextPath: 'jenkins_calci', onFailure: false, war: '**/*.war'
             echo "Deploy successful";
                
            }
        }
        
        }
    }

