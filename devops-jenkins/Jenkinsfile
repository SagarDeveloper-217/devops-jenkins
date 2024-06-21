
//--------------------------------first way------------------------------------------------

pipeline{
    agent any
    tools{
        maven 'maven3'
    }
    stages{
        stage('Build Maven'){
            steps{
              checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/SagarDeveloper-217/devops-automation']])
              bat 'mvn clean install'
            }
        }
        stage('Build Docker Image'){
            steps{
                script{
                    bat "docker build -t sagarlucky/devops-pro ."
                }
            }
        }
        stage('push image to hub'){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerc', variable: 'DOCKER_PASSWORD')]) {
                    bat "docker login -u sagarlucky -p ${DOCKER_PASSWORD}"
}
                     bat 'docker push sagarlucky/devops-pro'
   
                }
            }
        }
    }
}



//------------------------------second way-------------------------------------------


// pipeline {
//     agent any
    
//     environment {
//         DOCKER_IMAGE_NAME = 'sagarlucky/devops-pro'  // Docker image name
//         DOCKER_REGISTRY = 'docker.io'                // Docker Hub registry URL
//     }
    
//     tools {
//         maven 'maven3'
//     }
    
//     stages {
//          stage('Build Maven'){
//             steps{
//               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/SagarDeveloper-217/devops-automation']])
//               bat 'mvn clean install'
//             }
//         }
//         stage('Build Docker Image') {
//             steps {
//                 script {
//                  //   Ensure DOCKER_IMAGE_NAME is expanded correctly
//                     def dockerImage = "${DOCKER_IMAGE_NAME}".replaceAll('/', '_')
//                     bat "docker build -t ${dockerImage} ."
                    
//                 }
//             }
//         }
        
//         stage('Push Image to Docker Hub') {
//             steps {
//                 script {
//                     withCredentials([string(credentialsId: 'dockerc', variable: 'DOCKER_PASSWORD')]) {
//                         bat "docker login -u sagarlucky -p ${DOCKER_PASSWORD} ${DOCKER_REGISTRY}"
                        
//                     }
//                     bat "docker tag ${DOCKER_IMAGE_NAME} ${DOCKER_REGISTRY}/${DOCKER_IMAGE_NAME}"
//                     bat "docker push ${DOCKER_REGISTRY}/${DOCKER_IMAGE_NAME}"
                   
//                 }
//             }
//         }
//     }
// }

    
