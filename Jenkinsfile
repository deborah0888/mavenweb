pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'MAVEN_HOME'
    }

    stages {
        stage('git repo & clean') {
            steps {
                bat "rmdir /s /q mavenweb || exit 0"
                bat "git clone https://github.com/deborah0888/mavenweb.git"
                bat "mvn clean -f mavenweb/pom.xml"
            }
        }

        stage('install') {
            steps {
                bat "mvn install -f mavenweb/pom.xml"
            }
        }

        stage('test') {
            steps {
                bat "mvn test -f mavenweb/pom.xml"
            }
        }

        stage('package') {
            steps {
                bat "mvn package -f mavenweb/pom.xml"
            }
        }
    }
}
