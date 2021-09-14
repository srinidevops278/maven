pipeline
{
    agent any
    stages
    {
        stage('Continuous Download')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('Continuous Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Continuous Deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'afcef707-3a71-4010-8936-33bb5e9449ea', path: '', url: 'http://172.31.80.175:8080/')], contextPath: 'QAAPP!', war: '**\\*.war'
            }
        }
        stage('Continuous Testing')
        {
            steps
            {
             git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
             sh 'java -jar /var/lib/jenkins/workspace/pipeline-practice/testing.jar'   
            }
        }
        stage('Continuous Delivery')
        {
            steps
            {
             
            deploy adapters: [tomcat9(credentialsId: 'afcef707-3a71-4010-8936-33bb5e9449ea', path: '', url: 'http://172.31.92.65:8080/')], contextPath: 'PRODAPP!', war: '**\\*.war'
            }
        }
    }
}
