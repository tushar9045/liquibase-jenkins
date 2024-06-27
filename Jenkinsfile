pipeline {
    agent any

    environment {
        DATABASE_URL = 'jdbc:mysql://localhost:8082/db1'
        DATABASE_USERNAME = 'tushar'
        DATABASE_PASSWORD = 'tushar'
        LIQUIBASE_HOME = 'D:\\liquibase'
        JDBC_DRIVER_PATH = 'C:\\Users\\37095\\Downloads\\mysql-connector-j-8.4.0\\mysql-connector-java-8.4.0.jar'
    }

    stages {
        stage('Set up Liquibase') {
            steps {
                bat '"D:\\liquibase\\liquibase" --version'
            }
        }

        stage('Update Database') {
            steps {
                // Execute Liquibase update with embedded credentials
                bat """liquibase --changeLogFile=db/src/main/dbschema/master.xml \
                    --url=${env.DATABASE_URL} \
                    --username=${env.DATABASE_USERNAME} \
                    --password=${env.DATABASE_PASSWORD} \
                    --classpath=${env.JDBC_DRIVER_PATH} \
                    update"""
            }
        }

        stage('Run Tests') {
            steps {
                // Placeholder for running tests, if applicable
                bat 'echo "Running tests"'
                // You can add specific test commands here
            }
        }

        stage('Deploy') {
            steps {
                // Placeholder for deployment steps, if applicable
                bat 'echo "Deployment step"'
                // You can add specific deployment commands here
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

