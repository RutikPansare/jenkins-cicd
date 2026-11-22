
pipeline {
    agent any

    options {
        disableConcurrentBuilds()
    }

    triggers {
        pollSCM('H/5 * * * *')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validate') {
            steps {
                sh '''
                    if [ ! -s app/index.html ]; then
                        echo "ERROR: app/index.html is missing or empty"
                        exit 1
                    fi
                    echo "Validation successful"
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    mkdir -p build
                    tar -czf build/webapp.tar.gz -C app .
                    echo "Build completed"
                    ls -lh build/webapp.tar.gz
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    mkdir -p /var/jenkins_home/deploy
                    cp build/webapp.tar.gz /var/jenkins_home/deploy/
                    echo "Deployment completed"
                '''
            }
        }
    }

    post {
        success {
            echo 'SUCCESS: Pipeline completed successfully'
        }
        failure {
            echo 'FAILURE: Pipeline failed. Check console output.'
        }
    }
}

