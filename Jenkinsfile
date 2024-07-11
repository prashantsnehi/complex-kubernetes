pipeline {
    agent any
    environment {
        PROJECT_ID = 'multi-k8-428910'
        CLUSTER_NAME = 'multi-client'
        LOCATION = 'asia-south1-a'
        CREDENTIALS_ID = 'multi-k8s'
    }
    stages {
        stage("Checkout code") {
            steps {
                checkout scm
            }
        }
        // stage("Build image") {
        //     steps {
        //         script {
        //             myapp = docker.build("<<Your DockerHub username>>/hello:${env.BUILD_ID}")
        //         }
        //     }
        // }
        // stage("Push image") {
        //     steps {
        //         script {
        //             docker.withRegistry('https://registry.hub.docker.com', 'dockerID') {
        //                     myapp.push("latest")
        //                     myapp.push("${env.BUILD_ID}")
        //             }
        //         }
        //     }
        // }        
        stage('Deploy to GKE') {
            steps{
                sh "sed -i 's/hello:latest/hello:${env.BUILD_ID}/g' deployment.yaml"
                step([$class: 'KubernetesEngineBuilder', 
                    projectId: env.PROJECT_ID, 
                    clusterName: env.CLUSTER_NAME, 
                    location: env.LOCATION, 
                    manifestPattern: './k8s-single/deployment.yaml', 
                    credentialsId: env.CREDENTIALS_ID, 
                    verifyDeployments: true])
            }
        }
    }    
} 
