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
                // Execute Liquibase update with embedded credentials and JDBC driver path
                bat """D:\\liquibase\\liquibase --changeLogFile=db/src/main/dbschema/master.xml \
                    --url=${env.DATABASE_URL} \
                    --username=${env.DATABASE_USERNAME} \
                    --password=${env.DATABASE_PASSWORD} \
                    --classpath="${env.JDBC_DRIVER_PATH}" \
                    update"""
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

