pipeline {

    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK21'
    }

    stages {

        stage('Checkout') {

            steps {

                git branch: 'main',
                url: 'url: 'https://github.com/chethan6186/mvn1.git''

            }
        }

        stage('Build') {

            steps {

                bat 'mvn clean compile'

            }
        }

        stage('Test') {

            steps {

                bat 'mvn test'

            }
        }

        stage('Package') {

            steps {

                bat 'mvn package'

            }
        }

        stage('Run Application') {

            steps {

                bat 'mvn exec:java -Dexec.mainClass="com.example.app.App"'

            }
        }
    }

    post {

        success {

            emailext(
                subject: "SUCCESS: ${JOB_NAME} #${BUILD_NUMBER}",
                body: "Build succeeded!\nCheck: ${BUILD_URL}",
                to: "gowthamsgowtu@gmail.com"
            )
        }

        failure {

            emailext(
                subject: "FAILED: ${JOB_NAME} #${BUILD_NUMBER}",
                body: "Build failed!\nCheck: ${BUILD_URL}",
                to: "gowthamsgowtu@gmail.com"
            )
        }
    }
}
