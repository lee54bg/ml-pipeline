pipeline {
    agent { label 'ubuntu-slave1' }
    stages {
        stage('Environment Setup') {
            steps {
                sh 'echo "Setting up the environment"'
                sh 'python3 -m venv main'
                sh 'cd main \
                    && source bin/activate \
                    && pip install --upgrade pip \
                    && pip install sklearn \
                    && pip install pandas \
                '
            }
        }
        stage('Build') {
            steps {
                // sh 'echo "World"'
                sh 'python3 main/random_forest_classification.py'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Starting the test phase..."'
            }
        }
        stage('Cleanup') {
            steps {
                sh 'echo "Starting the cleanup phase..."'
                sh 'python3 removefiles.py'
                // sh '''
                //     echo "This should not go through"
                //     ls -lah
                // '''
            }
        }
    }
}
