
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
                sshagent(['73f77e93-ca9b-4876-b8b7-140e093ae799']) {
                    sh 'scp -o StrictHostKeyChecking=no target/*.war root@54.185.166.79:/root/apache-tomcat-9.0.118/webapps/'
                }
            }
        }
    }
}
