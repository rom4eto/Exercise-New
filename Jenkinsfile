pipeline{
    agent any

    environment{
        NODE_VERSIONS = '22.x'
    }

    tools{
        nodejs "${NODE_VERSIONS}"
    }

    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/rom4eto/Exercise-New'
            }
        }

        stage('Install dependencies'){
            steps{
                script{
                    
                    bat 'npm install'
                    
                }
            }
        }

        stage('Start application'){
            steps{
                script{
                    bat 'npm start &'
                    bat 'wait-on http://localhost:8090'
                    bat 'npm test'
                }
            }
        }
    }
    post{
        always{
            echo "CI pipeline completed"
        }
    }
}