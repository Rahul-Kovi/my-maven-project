pipeline
{
    agent any
    stages
    {
        stage('Download')
        {
            steps
            {
                git 'https://github.com/Rahul-Kovi/my-maven-project.git'
            }
        }
        stage('Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'be719646-cb63-4493-9261-b3caa2828b8f', path: '', url: 'http://43.205.103.245:8080')], contextPath: 'mytestapp', war: '**/*.war'
            }
        }
        stage('Testing')
        {
            steps
            {
                git 'https://github.com/Rahul-Kovi/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('Delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'be719646-cb63-4493-9261-b3caa2828b8f', path: '', url: 'http://172.31.35.73:8080')], contextPath: 'myprodapp', war: '**/*.war'
            }
        }
    }
}
