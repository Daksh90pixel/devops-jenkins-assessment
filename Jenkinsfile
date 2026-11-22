pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Source code checkout completed.'
            }
        }

        stage('Validate') {
            steps {
                sh '''
                    if [ ! -s app/index.html ]; then
                        echo "ERROR: app/index.html is missing or empty."
                        exit 1
                    fi
                    echo "HTML file validation successful."
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                    tar -czf app-build.tar.gz app/
                    echo "Application archive created."
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    mkdir -p "$JENKINS_HOME/devops-lab/deploy"
                    cp app-build.tar.gz "$JENKINS_HOME/devops-lab/deploy/"
                    echo "Application deployed to the test directory."
                '''
            }
        }
    }
}
