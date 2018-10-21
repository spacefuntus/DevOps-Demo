pipeline {
    agent {
        label "master"
    }
    tools {
        maven 'maven3'

    }
    stages {
        stage ('Initialize') {
            steps {
                bat '''
                    echo "PATH = %PATH%"
                    echo "M2_HOME = %M2_HOME%"
                '''
            }
        }
stages {
        stage ('Checkout') {
            steps {
                
            }
        }
        stage ('Build') {
            steps {
                    bat 'cd NumberGenerator & mvn install'
            }
             post {
                success {
                    junit 'NumberGenerator/target/surefire-reports/*.xml'
                        }
                 }



            }
        }

}

