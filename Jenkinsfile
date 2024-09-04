pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'git@github.com:praveen-kumar3122/test.git', branch: 'main'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build commands here, e.g., Maven, Gradle, etc.
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your testing commands here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Use the AWS CodeDeploy plugin or AWS CLI to deploy the app
                script {
                    // Example using AWS CodeDeploy plugin
                    def deployResult = awsCodeDeploy applicationName: 'test',
                                                      deploymentGroupName: 'testdg',
                                                      s3Bucket: 'code-deploye-b1',
                                                      s3Key: 'test.zip'
                    echo "Deployment result: ${deployResult}"
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            // Add any cleanup tasks if needed
        }
        success {
            echo 'Deployment succeeded!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
