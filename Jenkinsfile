pipeline {
    agent any
    tools {
       maven 'MAVEN_HOME'
       jdk 'JAVA_HOME'
        }

    stages {
        stage ('Compile Stage') {

            steps {
                    sh 'mvn clean compile'
            }
        }

        stage ('Testing Stage') {

            steps {
                    sh 'mvn test'
            }
        }


        stage ('Deployment Stage') {
            steps {
                    echo "Deploying"
            }
        }
    }
}
