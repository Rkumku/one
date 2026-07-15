
pipeline {
    agent any

    stages {
        stage('code checkout') {
            steps {
                git 'https://github.com/Rkumku/one.git'
            }
        }

        stage('maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('deploy') {
            steps {
                sshagent(['9d74b3de-7538-4450-939c-2bdaefc16bb9']) {
                    sh 'scp -o StrictHostKeyChecking=no target/*.war root@54.185.166.79:/root/apache-tomcat-9.0.118/webapps/'
                }
            }
        }
    }
}
