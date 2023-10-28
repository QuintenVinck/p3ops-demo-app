pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build and Publish .NET App') {
            steps {
                script {
                    // Use --password-stdin for secure password handling
                    withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                        def registry = 'https://registry.hub.docker.com'
                        
                        sh "echo \${DOCKER_PASSWORD} | docker login -u \${DOCKER_USERNAME} --password-stdin \${registry}"
                        sh "docker build -t quintenv/dotnet-app ."
                        sh "docker push quintenv/dotnet-app"
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
//                     // Use --password-stdin for secure password handling
//                     withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
//                         def registry = 'https://registry.hub.docker.com'
//                         sh "echo \${DOCKER_PASSWORD} | docker login -u \${DOCKER_USERNAME} --password-stdin \${registry}"
//                         sh "docker build -t quintenv/android-app ."
//                         sh "docker push quintenv/android-app"
//                     }
//                 }
//             }
//         }
//     }
// }
