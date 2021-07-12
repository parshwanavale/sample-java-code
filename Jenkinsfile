pipeline {
    agent any
    tools {
       maven 'MAVEN_HOME'
       jdk 'JAVA_HOME'
        }

    stages {
        stage ('Build Stage') {

            steps {
                    sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }

        stage ('Testing Stage') {

            steps {
                    sh 'mvn test'
            }
        }


        stage ('Deployment Stage') {
            steps {
                    deploy adapters: [tomcat9(credentialsId: '15a3ca3b-941a-41ed-9d6e-bbc1c3e569f3', path: '', url: 'http://192.168.16.247:8082/')], contextPath: 'rps', war: '**/*.war'
            }
            post{
                success{
                    emailext body: 'Deployment successful', compressLog: true, recipientProviders: [developers()], subject: 'Build result', to: 'krishna.tapdiya@afourtech.com'
                }
            }
        }
        
        
    }
}
