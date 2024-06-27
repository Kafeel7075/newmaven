pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
            deploy adapters: [tomcat9(credentialsId: '6f7261ca-d6af-4f8f-a27b-da5bf5383201', path: '', url: 'http://172.31.20.42:8080')], contextPath: 'mytestapp', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
            
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
               
                deploy adapters: [tomcat9(credentialsId: '6f7261ca-d6af-4f8f-a27b-da5bf5383201', path: '', url: 'http://172.31.16.93:8080')], contextPath: 'myprodapp', war: '**/*.war'
            }
        }
        
        
        
    }
}
