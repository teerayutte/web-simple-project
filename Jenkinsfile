pipeline{
    agent {
        docker {
            image 'docker:24.0.2'
            args '--privileged -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning repository...'
                sh 'rm -rf web-simple-project || true'
                sh 'git clone https://github.com/teerayutte/web-simple-project.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'docker build -t my-web-app .'
            }
        }
        stage('Run') {
            steps {
                echo 'Running...'
                sh 'docker rm -f my-web || true'
                sh 'docker run -d --name my-web -p 5000:80 my-web-app'
            }
        }
    }
}
