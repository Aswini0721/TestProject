
def tomcatWeb = 'http://localhost:9999/manager/text'

pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'Maven_Install') {
                    bat 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'Maven_Install') {
                    bat 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'Maven_Install') {
                    bat "copy target\\TestProject-0.0.1-SNAPSHOT.war  \"${tomcatWeb}\\TestProject-0.0.1-SNAPSHOT.war\""
                }
            }
        }
    }
}