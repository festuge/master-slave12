pipeline {
    agent {
        label{
            label 'slave1'
        }
    }
    stages{
        stage('version-control'){
            steps{
                git branch: 'main', credentialsId: 'github-id', url: 'https://github.com/festuge/master-slave12.git'
            }
        }
        stage('parallel-job'){
            parallel{
                stage('sub-job1'){
                    steps{
                        sh 'echo "action1"'
                    }
                }
                stage('sub-job2'){
                    steps{
                        sh 'echo "action2"'
                    }
                }
                stage('sub-job3'){
                    steps{
                        sh 'echo "action3"'
                    }
                }
            }
        }
        stage('codebuild'){
            agent{
                label{
                    label 'slave2'
                }
            }
            steps{
                sh 'cat /etc/passwd'
            }
        }
    }
}