pipeline {
    agent {
        label "master"
    }
    tools {
        maven 'Maven3'

    }
    stages {
        stage ('SET YOUR GOALS') {
            steps {
                sh '''
                    echo "PATH = $PATH"
                    echo "M2_HOME = $M2_HOME"
                '''
            }
        }

        stage ('PLAN YOUR GOALS') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/DPLExample']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/devops81/DevOps-Demo.git']]])
                
            }
        }
        
        stage ('START WORKING ON PLAN') {
            steps {
                dir("/var/lib/jenkins/workspace/Miscelleneous/10212018/examples/feed-combiner-java8-webapp") {
             sh 'mvn clean install'
                }
                
            }
        }
          stage ('KEEP PRACTICING') {
             steps {
                  parallel ( 
                      'FIRST FAILED': 
            {
                junit 'examples/feed-combiner-java8-webapp/target/surefire-reports/*.xml'
                
            },
                      'TRY AGAIN' :
                      {                  
                         emailext body: 'Junit reporting getting archived', subject: 'junit update', to: 'devops81@gmail.com'
                     }
                     )
            } 
        }
        stage ('YOU WILL BE NEAR TO SUCCESS') {
            steps {
               
                sh '/bin/cp  -rf  /var/lib/jenkins/workspace/Miscelleneous/10212018/examples/feed-combiner-java8-webapp/target/devops.war /home/ec2-user/tomcat/apache-tomcat-9.0.12/webapps/'
                
            }
        }
        stage ('KEEP WORKING SUCCESS NOTIFICATION WILL BE SENT ACROSS') {
            steps {
                emailext body: '$DEFAULT_CONTENT', subject: '$DEFAULT_SUBJECT', to: 'devops81@gmail.com'

                
            }
        }
        }
       
                      
}

