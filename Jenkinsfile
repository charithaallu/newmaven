node('master') 
{
    stage('continuousdownload')
    {
        git branch: 'main', url: 'https://github.com/charithaallu/maven.git'
    }
    stage('Continuousbuild')
    {
        sh 'mvn package'
    }
    stage('continuousdeployment')
    {
        deploy adapters: [tomcat9(credentialsId: '27e3ffa9-812c-4f13-ac39-5d786ac1bc70', path: '', url: 'http://3.98.141.163:8080')], contextPath: 'testing', war: '**/*.war'
    }
    stage('continuousTesting')
    {
        git 'https://github.com/charithaallu/FunctionalTesting-1.git'
        sh 'java -jar /var/lib/jenkins/workspace/scripted/testing.jar'
    }
    stage('Continuousdelivery')
    {
        deploy adapters: [tomcat9(credentialsId: '27e3ffa9-812c-4f13-ac39-5d786ac1bc70', path: '', url: 'http://35.183.7.116:8080')], contextPath: 'production', war: '**/*.war'
    }
}
