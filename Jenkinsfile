pipeline{

    agent any

    stages{

        stage('Run Test'){
            steps{
                bat "docker-compose up --scale chrome=2 --scale firefox=2"
            }
        }

        stage('Bring down grid'){

            steps{
                bat "docker-compose down --volumes"
                bat "docker system prune -f"
            }
        }
}