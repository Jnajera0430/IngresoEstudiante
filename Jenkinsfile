pipeline{
    agent any
    environment {
        DB_NAME = credentials('DB_NAME')
    }
    stages{
    	stage("Export secrets"){
            steps{
                script {
                    if (isUnix()) {
                        sh 'export DB_NAME=${DB_NAME}'
                    } else {
                        bat 'set DB_NAME=${DB_NAME}'
                    }
                }
            }
        }
        stage("Build Angular"){
            steps{
                script {
                    if (isUnix()) {
                        sh 'pnpm i'
                        sh 'pnpm run build'
                    } else {
                        bat 'pnpm i'
                        bat 'pnpm run build'
                    }
                }
            }
        }
    }
}