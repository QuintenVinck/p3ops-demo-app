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
                    withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                        def registry = 'https://registry.hub.docker.com'
                        def image = 'quintenv1/dotnet-app:latest'
                        
                        sh "echo \${DOCKER_PASSWORD} | docker login -u \${DOCKER_USERNAME} --password-stdin \${registry}"
                        sh "docker build -t \${image} -f Dockerfile ."
                        sh "docker push \${image}"
                    }
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
