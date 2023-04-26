pipeline {
    environment{
        version = '1.3.0'
    }
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
                echo $version
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
                checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/feature_gunjanm']], extensions: [], userRemoteConfigs: [[credentialsId: 'ibt', url: 'https://github.com/IBT-learning/ibt-maven.git']])
                sh 'ls -lrt'
                sh 'echo $Branch_Name $CHOICES'
                sh 'echo trying hook'
            }
        }
        stage('testing hooks') {
         environment{
                version2 = '1.5.0'
            }
                         steps {
                              echo 'hook tested success'
                              echo $version2
                           }
                       }
    }
}
