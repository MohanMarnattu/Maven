node('built-in') {
   stage('ContDownload') {
    git 'https://github.com/intelliqittrainings/maven.git'
}
    stage('ContBuild') {
    sh 'mvn package'
}
    stage('ContDeployment') {
    deploy adapters: [tomcat9(credentialsId: 'ce6a9820-6dfc-4c7e-a726-1229df0fc400', path: '', url: 'http://172.31.46.28:8080')], contextPath: 'path', war: '**/*.war'
}
    stage('ContTesting') {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh 'java -jar  /var/lib/jenkins/workspace/Scripted-Pipeline/testing.jar'
}
   stage('ContDelivary') {
   deploy adapters: [tomcat9(credentialsId: 'ce6a9820-6dfc-4c7e-a726-1229df0fc400', path: '', url: 'http://172.31.45.48:8080')], contextPath: 'path1', war: '**/*.war'
}
}
