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
                // bat "npx ng test --no-watch --no-progress --browsers=ChromeHeadless"
                echo "test"
            }
        }
        stage("build") {
            steps {
                bat "npx ng build --configuration production"
            }
        }
        stage("Deployment") {
            steps {
                bat "del /q /s c:\\inetpub\\wwwroot\\angularapp\\*"
                bat "xcopy /E /Y /I dist\\* c:\\inetpub\\wwwwroot\\angularapp\\"
            }
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
