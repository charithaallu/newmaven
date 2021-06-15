node('master') 
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/charithaallu/newmaven.git'             
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: '27e3ffa9-812c-4f13-ac39-5d786ac1bc70', path: '', url: 'http://3.98.122.72:8080')], contextPath: 'myfirstapp', war: '**/*.war'
    }

    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting1.git'
        sh 'java -jar /var/lib/jenkins/workspace/multibranch_main/testing.jar'
    }
    stage('ContinuousDelivery')
    {
    
        deploy adapters: [tomcat9(credentialsId: '27e3ffa9-812c-4f13-ac39-5d786ac1bc70', path: '', url: 'http://15.222.237.57:8080')], contextPath: 'myfirstapp', war: '**/*.war'
     }
}
