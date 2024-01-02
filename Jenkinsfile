pipeline  {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Clone the GitHub repository
                git branch: 'main', url: 'https://github.com/priyashinde09/django-notes-app'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                        sh "docker container prune -f"
                        sh "docker image prune -a -f"
                        sh "docker builder prune --all --force"
                        sh "docker system prune"
                        sh "docker build -t my-note-app ."
                    }
                }
            }
        stage('Push to DockerHub') {
            steps {
                script {
                    // Define the Docker Hub credentials ID
                    def dockerHubCredentialId = 'docker-cred'
                    def dockerImageName = "shivanu1608/my-note-app:${BUILD_NUMBER}"

                    // Authenticate with Docker Hub using the credentials
                    withCredentials([usernamePassword(credentialsId: dockerHubCredentialId, passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
                        sh """
                        docker login -u \${DOCKERHUB_USERNAME} -p \${DOCKERHUB_PASSWORD}
                        docker tag react-app shivanu1608/my-note-app:\${BUILD_NUMBER}
                        docker push ${dockerImageName}
                        """
                    }
                }
            }
        }
        stage("Deploy"){
            steps {
                script{
                echo "Deploying the container"
                sh "docker-compose down && docker-compose up -d"
                }
                
            }
        }
    }
}
