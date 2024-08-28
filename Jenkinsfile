pipeline {
    agent any

    tools { 
        maven 'Maven'
    }

    stages {
        stage('Initialize') {
            steps {
                sh '''
                echo "PATH = ${PATH}"
                echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy-To-Tomcat') {
            steps {
                sshagent(['tomcat']) {
                    sh '''
                    scp -o strictHostkeyChecking=no target/your-project-1.0-SNAPSHOT.jar ubuntu@15.206.124.53:/prod/apache-tomcat-10.1.28/webapps/webapp.war
                    '''
                }
            }
        }
    }
}
