pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'maven') {
                    sh 'mvn deploy'
                }
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            emailext attachLog: true, body: 'Build failed', presendScript: 'echo "Email Success"', subject: 'Build failed', to: 'karthikmahali@gmail.com'
        }
    }
}
