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
        
        stage('Build .NET Project') {
            steps {
                // Use dotnet CLI to build the project
                sh 'dotnet build'
            }
        }
        
        stage('Push to Docker Hub') {
            steps {
                // Build and push Docker image
                script {
                    docker.build('mcr.microsoft.com/dotnet/sdk:6.0:latest', '.')
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                        docker.image('mcr.microsoft.com/dotnet/sdk:6.0:latest').push()
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
