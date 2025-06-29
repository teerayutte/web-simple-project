pipeline{
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository...'
                bat 'git clone https://github.com/teerayutte/web-simple-project.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                bat 'docker build -t my-web-app .'
            }
        }
        stage('Run') {
            steps {
                echo 'Running...'
                bat 'docker rm -f my-web || true'
                bat 'docker run -d --name my-web -p 8088:80 my-web-app'
            }
        }
    }
}
