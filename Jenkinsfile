pipeline{

    agent any

    stages{

        stage('Cleanup Previous Containers') {
            steps {
                bat 'docker-compose down --volumes || echo "No previous containers to remove"'
                bat 'docker system prune -f'
            }
        }


        stage('Run Test'){
            steps{
                bat "docker-compose up --scale chrome=2 --scale firefox=2"
            }
        }

        stage('Bring down grid'){

            steps{
                bat "docker-compose down"
            }
        }
    }
}