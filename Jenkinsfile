pipeline{

    agent any

    stages {

        stage('start grid') {
            steps {
                bat 'docker-compose -f grid.yaml up'
            }
        }

        stage('start test') {
                    steps {
                        bat 'docker-compose up'
                    }
                }

        stage('Bring grid down') {
            steps {
                bat 'docker-compose down'
            }
        }

    }

}