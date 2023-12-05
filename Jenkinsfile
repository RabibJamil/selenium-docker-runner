pipeline{

    agent any

    parameters {
      choice choices: ['chrome', 'firefox'], description: 'Select the browser', name: 'Browser'
    }

    stages{

        stage('Start Grid'){
            steps{
                bat "docker-compose -f grid.yaml up -d"
            }
        }

        stage('Run Test'){
            steps{
                bat "docker-compose -f test-suites.yaml up"
            }
        }

    }

    post {
        always {
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
            archiveArtifacts artifacts: 'Users/rabib/VolumeSharing/output/flight-reservation/emailable-report.html', followSymlinks: false
            archiveArtifacts artifacts: 'Users/rabib/VolumeSharing/output/vendor-portal/emailable-report.html', followSymlinks: false
        }
    }

}