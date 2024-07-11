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
                        --username=${env.USERNAME} \
                        --password=${env.PASSWORD} \
                        --changeLogFile=db/src/main/dbschema/master.xml \

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