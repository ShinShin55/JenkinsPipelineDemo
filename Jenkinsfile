pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from GitHub commit trigger'
            }
        }
        stage('Build') {
            steps {
                echo 'Building'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws cp /var/lib/jenkins/workspace/JenkinsPipeline/index.html /home/ec2-user/test/')
                    }
                }
        }
        stage('Test') {
            steps {
                echo 'testing'
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing'
            }
        }
    }
}
