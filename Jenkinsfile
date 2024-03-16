 pipeline
   {
  agent any
  
    stages{
        stage('ContDownload'){
            steps{
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContBuild'){
            steps{
                sh 'mvn package'
            }
        }
         stage('ContDeployment'){
            steps{
               deploy adapters: [tomcat9(credentialsId: 'ce6a9820-6dfc-4c7e-a726-1229df0fc400', path: '', url: 'http://172.31.46.28:8080')], contextPath: 'path', war: '**/*.war'
            }
        }
        stage('ContTesting'){
            steps{
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DEC/testing.jar'

            }
        }
       stage('ContDelivary'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'ce6a9820-6dfc-4c7e-a726-1229df0fc400', path: '', url: 'http://172.31.45.48:8080')], contextPath: 'path1', war: '**/*.war'
            }
        }
    }     
  }       
