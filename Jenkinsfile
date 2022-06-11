pipeline {
    agent any
    stages {
        stage('1-version-control'){
            steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '27ad29e6-be3a-49fa-8285-afa75c144e11', url: 'https://github.com/etechpipeline/team3multibuild.git']]])
            }
        }
        stage('2-parallel-job'){
            parallel{
                stage('sub-job-1'){
                    steps{
                        sh 'uptime'
                        sh 'ls -lrt'
                    }
                }
                stage('sub-job-2'){
                    steps{
                        sh 'ps -ef'
                        sh 'free -g'
                    }
                }
                stage('sub-job-3'){
                    steps{
                        sh 'df -h'
                        sh 'lscpu'
                    }
                }
            }
        }
        stage('3-Stage-Deployment-Prod'){
            when{
                branch 'develop'
            }
            steps{
                sh 'cat /stc/passwd'
                sh 'echo " Deploy App from NonProd Evn all the way to Prod'
            }
        }
    }
}        