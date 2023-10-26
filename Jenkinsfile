pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your Git repository
                script {
                    checkout scm
                }
            }
        }
        
        // stage('Build .NET Project') {
        //     steps {
        //         // Use dotnet CLI to build the project
        //         sh 'dotnet build'
        //     }
        // }

        stage('Build and Dockerize') {
            steps {
                // Use Docker to build an image using the Dockerfile
                script {
                    docker.build('p3ops-demo-app:latest', '.')
                }
            }
        }

        
        stage('Push to Docker Hub') {
            steps {
                // Build and push Docker image
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'DockerHub2') {
                        docker.image('p3ops-demo-app:latest').push()
                    }
                }
            }
        }
    }
}

// pipeline {
//     agent any
    
//     stages {
//         stage('Checkout') {
//             steps {
//                 script {
//                     checkout scm
//                 }
//             }
//         }
        
//         stage('Build Android Project') {
//             steps {
//                 // Use Gradle to build the Android project
//                 sh './gradlew build'
//             }
//         }
        
//         stage('Push to Docker Hub') {
//             steps {
//                 script {
//                     docker.build('your-android-image:latest', '.')
//                     docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
//                         docker.image('your-android-image:latest').push()
//                     }
//                 }
//             }
//         }
//     }
// }
