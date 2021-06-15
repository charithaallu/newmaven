pipeline {
    agent any
    stages {
        stage('continuousdownload')
        {
            steps
            {
                git branch: 'main', url: 'https://github.com/charithaallu/maven.git'
            }
        }
        stage('continuousbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Continuousdeployment')
        {
            steps 
            {
                sh 'scp /var/lib/jenkins/workspace/declarative/webapp/target/webapp.war ubuntu@172.31.4.46:/var/lib/tomcat9/webapps/primeapp.war'
            }
}
