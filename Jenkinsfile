pipeline {
    agent any

    stages {
        stage('Test Docker') {
            steps {
                script {
                    sh 'docker --version'
                    sh 'docker image ls'
                }
            }
        }
    }
}


//dotnet
// pipeline {
//     agent any

//     stages {
//         stage('Checkout') {
//             steps {
//                 checkout scm
//             }
//         }

//         stage('Test Docker') {
//             steps {
//                 script {
//                     docker.image('hello-world').run()
//                 }
//             }
//         }

//         stage('Build and Publish .NET App') {
//             steps {
//                 script {
//                     docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
//                         def image = docker.build('quintenv1/dotnet-app:latest', '-f Dockerfile .')
//                         image.push()
//                     }
//                 }
//             }
//         }
//     }
// }





//android
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
