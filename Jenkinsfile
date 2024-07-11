pipeline {
    agent any

    environment {
        LIQUIBASE_DRIVER = 'com.mysql.cj.jdbc.Driver'
        LIQUIBASE_URL = credentials('db_url')
        USERNAME = credentials('db_username')
        PASSWORD = credentials('db_password')
    }


stages{
     stage('Liquibase Update') {
            steps {
                script {
                    // Construct Liquibase command with credentials directly in sh step
                    sh """
                    liquibase --driver=${env.LIQUIBASE_DRIVER} \
                        --url=${env.LIQUIBASE_URL} \
                        --username=${env.LIQUIBASE_USERNAME} \
                        --password=${env.LIQUIBASE_PASSWORD} \
                        update
                    """
                }
            }
        }
}        
     post {
        always {
            cleanWs()
        }
    }    

}    