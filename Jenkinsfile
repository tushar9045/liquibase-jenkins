pipeline {
    agent any
    
    environment {
        DATABASE_URL = 'jdbc:mysql://localhost:8082/db1'
        DATABASE_USERNAME = 'tushar'
        DATABASE_PASSWORD = 'tushar'
        LIQUIBASE_HOME = 'D:\\liquibase'
    }
    
    stages {
        stage('Set up Liquibase') {
            steps {
                withEnv(["PATH+LIQUIBASE=${LIQUIBASE_HOME}/bin"]) {
                    sh 'liquibase --version'
                }
            }
        }
        
        stage('Update Database') {
            steps {
                sh "liquibase --changeLogFile=db/src/main/dbschema/master.xml --url=${DATABASE_URL} --username=${DATABASE_USERNAME} --password=${DATABASE_PASSWORD} update"
            }
        }
        
        stage('Run Tests') {
            steps {
                sh 'echo "Running tests"'
                // Add specific test commands here if applicable
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'echo "Deployment step"'
                // Add deployment commands here if applicable
            }
        }
    }
    
    post {
        always {
            cleanWs()
            echo "Pipeline finished"
        }
    }
}

