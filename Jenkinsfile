pipeline{

    agent any

    stages{

        stage('Start-Grid') {
            steps {
                bat "docker-compose -f grid.yaml up -d"
            }
        }


        stage('Run Test'){
            steps{
                bat "docker-compose -f test-suites.yaml up"
            }
        }
    }
    post{
        always{
            bat "docker-compose -f grid.yaml down"
            bat "docker-compose -f test-suites.yaml down"
            bat 'xcopy /E /Y "D:\\Project\\selenium-docker-master\\selenium-docker-master\\03-automation-framework\\selenium-docker\\test-output-results\\" "D:\\Project\\selenium-docker-master\\selenium-docker-master\\03-automation-framework\\selenium-docker\\volume\\node\\workspace\\SELENIUM_DOCKER_RUNNER"'
            archiveArtifacts artifacts: 'flight-reservation/emailable-report.html', followSymlinks: false
            archiveArtifacts artifacts: 'vendor-portal/emailable-report.html', followSymlinks: false

        }
    }
}