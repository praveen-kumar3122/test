pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                awsCodeDeploy(
                    applicationName: 'your-application-name',
                    deploymentGroupName: 'your-deployment-group-name',
                    deploymentConfigName: 'CodeDeployDefault.OneAtATime',
                    description: 'Deployment description',
                    waitForCompletion: true
                )
            }
        }
    }
}
