pipeline {
    agent {
        label "master"
    }
    tools {
        maven 'Maven3'

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

        stage ('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/DPLExample']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/devops81/DevOps-Demo.git']]])
                
            }
        }
       
    }                   
}

