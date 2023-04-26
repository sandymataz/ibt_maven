pipeline {
    agent any
        stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Hi') {
            steps {
                echo 'Hi'
            }
        }
         stage('test') {
            steps {
                echo 'test'
            }
        }
        stage('testing jenkinsfile') {
        when{
            expression{
                env.BRANCH_NAME=='main'
            }
        }
                 steps {
                      echo 'jenkinsfile'
                   }
               }
        stage('Git checkout') {
            steps{
                checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/$Branch_Name']], extensions: [], userRemoteConfigs: [[credentialsId: 'ibt', url: 'https://github.com/IBT-learning/ibt-maven.git']])
                sh 'ls -lrt'
                sh 'echo $Branch_Name $CHOICES'
                sh 'echo trying hook'
            }
        }
        stage('testing hooks') {
                         steps {
                              echo 'hook tested success'
                           }
                       }
    }
}
