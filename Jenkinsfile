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
                sh '''
                scp -i /var/lib/jenkins/.ssh/id_rsa -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.9.170:/tmp/
                ssh -i /var/lib/jenkins/.ssh/id_rsa -o StrictHostKeyChecking=no ec2-user@172.31.9.170 "sudo cp /tmp/myweb.war /root/apache-tomcat-9.0.118/webapps/"
                '''
            }
        }
    }
}
