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
                    applicationName: 'test',
                    deploymentGroupName: 'testdg',
                    deploymentConfigName: 'CodeDeployDefault.OneAtATime',
                    description: 'Deployment description',
                    waitForCompletion: true
                )
            }
        }
    }
}
