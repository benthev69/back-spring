pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage ("Clean up") {
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo") {
            steps {
                sh "git clone https://github.com/benthev69/back-spring.git"
            }
        }
        stage ("Generate backend image") {
            steps {
                dir("exp4spring") {
                    sh "mvn clean install"
                    sh "docker build -t exp4spring ."
                }
            }
        }
        stage ("Run docker compose") {
            steps {
                dir("exp4spring") {
                    sh "docker compose up -d"
                }
            }
        }
    }
}
