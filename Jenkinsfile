pipeline {
    agent any
    stages{
        stage('build project'){
            steps{
                git url:'https://github.com/sujitharamesh1998/project1', branch: "master"
                sh 'mvn clean package'
              
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t sujitha202301/staragileprojectfinance .'
                    sh 'docker images'
                }
            }
        }
        stage('docker login'){
             steps{
                 withCredentials([usernamePassword(credentialsId: 'dockerhub-pwd', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                sh "echo $PASS | docker login -u $USER --password-stdin"
                sh 'docker push sujitha202301/staragileprojectfinance'
                 }
             }
         }
         
        
        stage('Deploy') {
            steps {
                sh 'sudo docker run -itd --name My-first-containe21211 -p 8083:8081 sujitha202301/staragileprojectfinance'
                  
                }
            }
        
    }
}
