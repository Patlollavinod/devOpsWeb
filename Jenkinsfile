pipeline{
    agent {
        label 'linuxagent'
    }
    tools{
        maven 'maven3.8.2'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: [tomcat9(credentialsId: 'fc524f3e-f702-4df4-b2b6-cdf2ca3ded40', path: '', url: 'http://13.234.186.148:8080/')], contextPath: null, war: '**/*.war'
                

                echo "Deployment"
            }
        }
    }
}
