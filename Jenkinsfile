pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                bat ''' python --version
                        python -m venv env    
                '''
                bat 'env/Scripts/activate'
            }
        }
    }
}
