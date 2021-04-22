pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                bat ''' python --version
                        python -m venv env    
                '''
                bat '''env/Scripts/activate
                       pip install -r mysite/requirements.txt
                '''
            }
        }
        stage('test') {
            steps {
                bat 'py mysite/manage.py test polls'
            }
        }
        stage('deploy') {
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                    bat 'py mysite/manage.py runserver'
                }
                
            }
        }
    }
    post {
        success {
            echo 'Succeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
