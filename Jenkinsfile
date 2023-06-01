pipeline{
    agent any
    environment {
        DB_NAME = credentials('DB_NAME')
    }
    stages{
    	stage("Export secrets"){
            steps{
                script {
                    // if os windows export env variable DB_NAME
                    if (isUnix()) {
                        sh 'export DB_NAME=${DB_NAME}'
                    } else {
                        bat 'set DB_NAME=${DB_NAME}'
                    }
                }
            },
        }
        // stage
        stage("Build Angular"){
            steps{
                // build angular
                sh 'npm install'
                sh 'npm run build'
            },
        }
    }
}