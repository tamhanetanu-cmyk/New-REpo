pipeline {
    agent any
    tools {
        nodejs "NodeJs"
    }
    stages {
        stage("checkout") {
            steps {
                checkout scm
            }
            
        }
        stage("install package") {
            steps {
                bat "npm ci"
            }
        }
        stage("testing") {
            steps {
                bat "npx ng test --no-watch --no-progress --browsers=ChromeHeadless"
            }
        }
        stage("build") {
            steps {
                bat "npx ng build --configuration production"
            }
        }
        post {
            success {
                echo "agular application build successfully"
            }
            failure {
                echo "angular app build failed"
            }
        }
    }
}