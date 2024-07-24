pipeline {
    agent any

    environment {
        LIQUIBASE_DRIVER = 'com.mysql.cj.jdbc.Driver'
        LIQUIBASE_URL = credentials('db_url')
        USERNAME = credentials('db_username')
        PASSWORD = credentials('db_password')
        JDBC_DRIVER_PATH = '/var/lib/jenkins//workspace/liquibase_main/mysql-connector-j-8.4.0.jar' 
    }


stages{
     stage('Liquibase Update') {
            steps {
                script {
                    // Construct Liquibase command with credentials directly in sh step
                    sh """
                    liquibase --driver=${env.LIQUIBASE_DRIVER} \
                        --classpath=${env.JDBC_DRIVER_PATH} \
                        --url=${env.LIQUIBASE_URL} \
                        --username=${env.USERNAME} \
                        --password=${env.PASSWORD} \
                        --changeLogFile=${WORKSPACE}/db/src/main/dbschema/master.xml \
                        updatesql
                    """
                }
            }
        }
} 
         
        
    
}    
