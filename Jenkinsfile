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
                bat '"D:\\liquibase\\liquibase" --version'
            }
        }

        stage('Update Database') {
            steps {
                bat """
                    D:\\liquibase\\liquibase --changeLogFile=db/src/main/dbschema/master.xml \
                    --url=${env.DATABASE_URL} \
                    --username=${env.DATABASE_USERNAME} \
                    --password=${env.DATABASE_PASSWORD} \
                    --classpath=mysql-connector-java-8.4.0.jar \
                    update
                """
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

