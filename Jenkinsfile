pipeline {
    environment{
        version = '1.3.0'
    }
    tools {
        maven 'maven_3.8'
    }
    agent {label 'UX_IBT'}

        stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Hi') {
            steps {
                echo 'Hi'
                echo "${env.version}"
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
                              echo "${env.version2}"
                           }
                       }
         stage('mvn version') {
                     steps {
                         sh 'mvn --version'
                     }
                 }
    }
    post{
        always{
            emailext body: 'test', subject: 'test', to: 'gunjanvm7@gmail.com'
            echo "Build successful"
        }
    }
}
