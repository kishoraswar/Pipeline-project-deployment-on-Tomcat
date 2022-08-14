pipeline {  
   agent any
    stages {  
            stage ('Git-Checkout') {  
                steps{
                    git 'https://github.com/kishoraswar/Pipeline-project-deployment-on-Tomcat.git'
                    echo "Checkout successful";
                } 
            }
            stage ('Compile') {  
                  steps{
                    bat label: '', script: 'mvn compile'
                    echo "test successful";
                    
                } 
            }
            stage ('Build') {  
                  steps{
                    bat label: '', script: 'mvn clean'
                    bat label: '', script: 'mvn package'
                    echo "build successful";
                    
                } 
            }
             stage ('Test') {  
                  steps{
                    bat label: '', script: 'mvn test'
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

