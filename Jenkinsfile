pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/shamashaik19/healthcare.git'
                 echo 'github url checkout'
            }
        }
        stage('compile'){
            steps{
                echo 'starting compiling'
                sh 'bash -c "mvn compile"'
            }
        }
        stage('codetesting'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg1 .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 2000:8082 --name c000 myimg1'
            }
        }   
    }
}
